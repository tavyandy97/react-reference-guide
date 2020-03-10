# Props

Tags: props

Props are the basic data elements and functions that are passed onto any component by its parent component.

    <Person name={string} changed={func}>{inside}</Person>

The props if have to be accessed inside a class based are accessed using the this keyword, whereas in a functional component they are accessed directly.

    const person = (props) => {
    	return (
    		<div onclick={props.changed}>{props.name}</div>
    	)
    }

    class Person extends Component{
    	render(){
    		return(
    			<div onclick={this.props.changed}>{this.props.name}</div>
    		);
    	}
    }

In a class based component the props are accessed by using the `this` keyword.

If you want to access the elements inside the component. In the above case the element `inside` would be accessed by the component by using props.children.