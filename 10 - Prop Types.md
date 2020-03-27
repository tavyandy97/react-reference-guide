# Prop-Types

Tags: PropTypes, prop-types, props

In case you are creating components that will be used by other people, then it is recommended that you declare the prop types. `prop-types` is a third party package that restricts the props that can be passed to your component and their data types. Please look at their advanced usage on the [repository link](https://www.npmjs.com/package/prop-types).

    import PropTypes from 'prop-types';
    // The following code is for a class based component and is written 
    // below and outside the component
    Person.propTypes = {
    	clock: PropTypes.func,
    	name: PropTypes.string
    }