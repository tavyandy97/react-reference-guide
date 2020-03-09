# Components

Tags: class based, component, functional

A basic component in React can be of two types - functional or class based.
A functional component would look something like this

    import React from 'react';
    const app = (props) => {
    	return (<div>HelloWorld</div>);
    }
    
    export default app;

You might notice the div that the function returns isn't inside quotes. This is because we use JSX in React instead of JS. JSX helps us to ease out the syntax by giving us the functionality to write HTML like code in JS. 

Further the transpiler, converts the code from JSX to pure JS so it can be interpreted by the browser.
Whereas a class based component would look something like this 

    import React, {Component} from 'react';
    class App extends Component{
    	render(){
    		return (<div>HelloWorld</div>);
    	}
    }
        
    export default App;

The Component is a part of the React package. It gives us the functionality to create a class based component by extending itself.
**React keeps 2 copies of the DOM. One is the virtual DOM, which it creates before re-rendering any component, while the other one is the actual DOM, which is the current state of the DOM being shown in the browser. Remember whenever a component is called for render, React compares its rendered virtual DOM with the actual previous DOM, and only changed the components that are different.**
If we write JS inside of JSX we put it inside curly braces. eg `{5+2}`. *Inside of the curly braces it is recommended to use inline code (like ternary operators) instead of block like code (like if-then-else).*