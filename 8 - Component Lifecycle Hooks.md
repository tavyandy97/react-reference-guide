# Component Lifecycle Hooks

Tags: components, hooks, lifecycle

# Creation Lifecycle Hooks

- Creation Lifecycle Hooks
    - `constructor(props)`: In this we call `super(props)` (necessary) setup the state(optional).
    - `getDerivedStateFromProps(props,state)`: Whenever props are changed this function runs. Inside this function you sync the state to the props.
    - `render()`: It calls the creation lifecycle hooks for its children. Then it prepares the JSX and the corresponding structure.
    - `componentDidMount()`: After the component was successfully rendered, this function runs and here we cause side-effects. However, state change is not recommended.
- Updation Lifecycle Hooks
    - `getDerivedStateFromProps(props,state)`: Whenever props are changed this function runs. Inside this function you sync the state to the props.
    - `shouldComponentUpdate(nextProps , nextState)`: Returns a boolean, which decides whether the update should take place or not.
    - `getSnapshotBeforeUpdate(prevProps , prevState)`: Returns a copy of the state before updating it.
    - `render()`:It calls the updation lifecycle hooks for its children. Hence, re-rendering the component, by comparing virtual and actual DOM.
    - `componentDidUpdate()`: Executes post render after updation. You can cause side-effects here. However, state change is not recommended.
    - `componentWillUpdate` and `componentWillRecieveProps` are some lifecycle hooks that are extremely rarely used.

`componentWillUnmount()` is a lifecycle hook that is used as a destructor, or in other words used for clean-up, post the removal of a component.

For implementing the lifecycle hooks in functional components, the `useEffect` hook is used. The function runs after each re-render. It has one essential and one optional argument. `useEffect(() => {} , [])` the first argument being a function, while the second being an array. Cases for the second argument:

1. **No second argument:** The callback function will run on mount and everytime any variable is changed
2. **Empty Array as second argument:** The callback function will run only on mount.
3. **Non-Empty Array as second argument:** The callback function will run on mount and on every time the variables mentioned in the array are changed.