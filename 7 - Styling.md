# Styling

Tags: Radium, css, css modules, styling

# Basic Styling

The attribute `class` is not valid for components in React. The attribute `className` is used instead. This causes inline styling of components.

    <div className="red black-text">My name is Tavy</div>

Another alternative to the above method is to create a javascript object and inject that into the component.

    let style = {
    	color: 'blue',
    	backgroundColor : 'red'
    }
    <div style={style}>My name is Tavy</div>

Radium is a third party package, that provides us with a higher order component. This higher order component enables us to use pseudo-CSS selectors. Also if you are using media queries in your styling, wrap your component inside `<StyleRoot>`.

    var styles = {
    	color: 'red',
    	':hover': {
    		color: 'blue'
    	}
    }
    export default Radium(App);

# CSS Modules

Before adding CSS modules, make sure if you're using git, your whole repository is added and committed. Then run the command `npm eject`. Now navigate to `config\webpack.config.dev.js` and alter the css loader. Do the same for `config\webpack.config.prod.js`.

    modules: true,
    localIndentName: '[name]__[local]__[hash:base64:5]'

Initially we were `import './App.css'`, but now we shall `import classes from './App.css'`. This transforms the CSS into a javascript object named `classes`.