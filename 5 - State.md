# State

Tags: class based, container, functional, state

State is the information that is currently pertaining to the component being dealt with.
Class based components have the concept of state inbuilt into them. Hence the function `setState` can be called at any point of time where we seek to change the state.

    // Set state with a varibale
    this.setState({...JavaScriptObject})
    // Set state with prevState Object
    this.setState(prevState => {
    	return { property: prevState.property }
    })

However, if we want to manage state inside functional components then we have to use React Hooks. In this case specifically by the name of 'useState'.

    [state , setState] = useState(prevState);

The function useState returns an array of two elements - state and the function that can be used to alter that state.

Always try to create a copy of the existing state and alter the copy and then pass that as the new desired state.

In functional components it is recommended that we use the `useState` function multiple times for different parts of the state and manage them separately. This is done to avoid altering the original state. ***Stateful components are called Containers.*
If multiple functions are being called in sequence while setting a new state, you might want to pass the set state from one function to the following function. As sometimes the old state is obtained by the following function.**