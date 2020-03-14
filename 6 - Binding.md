# Binding

Tags: binding, data binding

# Passing arguments to functions *(that are being passed as props)*

Whenever a function is passed as props, only its reference is passed.

    const func = () => returnsSomething;
    <Person name={string} changed={func}>{inside}</Person>

In the case we want to pass an argument, there are two ways :

    const func = (props) => returnsSomething;
    <Person name={string} changed={() => func(xyz)}>{inside}</Person>

You can create an inline function, that calls the function after supplying with the desired arguments. However this isn't the approach that is considered the best. The better approach is:

    const func = (props) => returnsSomething;
    <Person name={string} changed={() => this.func.bind(this,xyz)}>{inside}</Person>

# Data Binding (One way)

Data binding in React can be done by passing a state-setting function to the child component as one of the props. Whenever the function is called, the state is changed and hence the parent component is re-rendered, in turn the child is re-rendered.