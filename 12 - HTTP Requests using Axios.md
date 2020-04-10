# HTTP Requests using Axios

Tags: axios, http

Axios is a library that will help us fetch data from API's. It is an async library and hence can't store data. Axios returns a [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) while making a request. Install it using `$ npm install --save axios`. 

The lifecycle hook during creation where we can cause side effects is `componentDidMount`. The lifecycle hook during updation where we can cause side effects is `componentDidUpdate`. It is not recommended that you update state in these two hooks, since it will cause an infinite loop. Hence if we do change the state, we do some checks.

    import axios from 'axios';
    
    // Making a GET request
    axios.get(url , object)
    	.then(callbackFunction)
    	.catch(callbackFunction);
    
    // Making a POST request
    axios.post(url , object)
    	.then(callbackFunction)
    	.catch(callbackFunction);
    // Similary for other HTTP methods

For common tasks to be done before or after a request is made via axios we use interceptors. These interceptors should be written in the `index.js` file so that they can be made common to all requests sent.

## Interceptors and Default Parameters

    // Before sending a request
    axios.interceptors.request.use(req => {
    	// Do task here
    	return req; 
    	// Important to return the request or request will remain pending
    } , err => {
    	// Do task here
    	return Promise.reject(err); 
    	// Important to reject the request or request will remain pending
    });
    
    // Before accepting a response
    axios.interceptors.response.use(res => {
    	// Do task here
    	return res; 
    	// Important to return the response or response will remain pending
    } , err => {
    	// Do task here
    	return Promise.reject(err); 
    	// Important to reject the response or response will remain pending
    });
    
    // Axios Defaults
    axios.defaults.baseURL = url;
    axios.defaults.headers.common['Authorization'] = auth;
    axios.defaults.headers.post['Content-Type'] = 'application/json';

If any request should not obey these default rules we create an instance of axios and import that for those specific requests.

    import axios from 'axios';
    
    **const inst = axios.create({
    	baseURL: newURL
    });**
    
    axios.defaults.headers.common['Authorization'] = auth;
    
    **export default inst;**

If we set axios interceptors in a re-usable or higher order component, there will be many useless instances of axios in the memory with interceptors initialized. Hence these interceptors should be removed.

    // Save instances to the interceptors in variables
    this.reqInterceptor = axios.interceptors.request.use(req => {
    	// Function Body
    	return req;
    });
    this.resInterceptor = axios.interceptors.response.use(
      callbackFunction,callbackFunction
    );
    
    // Later in the destructor (componentWillUnmount)
    axios.interceptors.request.eject(this.reqInterceptor);
    axios.interceptors.response.eject(this.resInterceptor);
    // Eject the respective interceptors to clear memory