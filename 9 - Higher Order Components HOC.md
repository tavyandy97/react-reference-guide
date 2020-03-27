# Higher Order Components (HOC)

Tags: Error, Error Boundary, Fragment, HOC, Higher Order Components, Memo, Pure Component

Higher Order Components are components that take components and return new components. They are based on the component re-usability principle of React.

# Error Boundary

Wrapping your component inside a higher order component like `<ErrorBoundary></ErrorBoundary>`. This catches the error if one is thrown. Hence, can be used where you know that an error may be thrown. However, it's performance is not that great, so don't wrap every component with it. `static getDerivedStateFromError()` or `componentDidCatch()` are triggered when error is caught. `static getDerivedStateFromError()` is used to render a fall-back UI. `componentDidCatch()` is used to log information.

    static getDerivedStateFromError(error) {
      // Update state so the next render will show the fallback UI.
      return { hasError: true };
    }
    
    componentDidCatch(error, errorInfo) {
      // You can also log the error to an error reporting service
    	logErrorToMyService(error, errorInfo);
    }

# Psuedo Wrapper

React doesn't allow a component to return multiple adjacent components. Adding an additional `<div>` might create undesirable results and hence we create an auxiliary higher order component.

    const aux = (props) => props.children;
    // Instead of the above functional component you can use the inbuilt feature in react
    <React.Fragment>
    	<YourComponent>
    </React.Fragment>

    // To write a functional higher order component
    const hoc = (MyComponent) => {
    	return props => {
    		<MyComponent/>
    	}	
    }

React only lets you return one parent element unless you are returning an array. If we refuse to use any of the above methods we can use the following method to return multiple adjacent components.

    render(){
    	return <div></div>,
    					<div></div>,
    					<div></div>
    }

# Pure Component

If you want to create a component that automates whether any of the props have changed and then only re-render, then use `<PureComponent></PureComponent>`. It automatically runs a `shouldComponentUpdate` for all the props.

# React.memo

A higher order component which memorizes all the props. Then whenever a re-render is called, the component is only re-rendered if any of the props are different from the previous ones. It is used as `React.memo(myComponent , areEqual)`. Where `areEqual` is a function being passed as an optional argument. This function optimizes the comparison of previous and next props.