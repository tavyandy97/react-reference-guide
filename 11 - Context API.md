# Context API

Tags: context

After a certain extent, managing props level after level of components becomes very difficult. React has an inbuilt solution to this, that is the Context API.
We create a component that is initialized with the default context.
`const MyContext = React.createContext(defaultValue);`
The component which somehow populates the context will be wrapped as follows:

    <MyContext.Provider value={{
    	something: this.something	
    }}>
    	<MyComponent></MyComponent>
    </MyContext.Provider>

Now the context values are made available inside the MyComponent and can be accessed as:

    render(){
    	return 	<MyContext.Consumer>
    		{context => context.something}
    	</MyContext.Consumer>
    }

However if we have to access the context inside a hook it becomes impossible. The better way to access context is to add `static contextType = MyContext;` to my class based component.
This makes the context available throughout the class based component as `this.context`.

To access context inside a functional component, we use the `useContext` hook. Further all the parts of context can be accessed by the returned variable by `useContext`.

    const myContext = useContext(MyContext);