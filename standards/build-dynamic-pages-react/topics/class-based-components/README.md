# React: Class-Based Components

```jsx
import React, { Component } from "react"

class SomeComponent extends Component {
  state = {
    someProperty: "Some Value"
  }

  someComputedProperty = () => {
    return this.props.someProp.map(item => (
      <p>{item}</p>
    )
  }

  componentDidMount = () => {
    fetch("http://someurl.com")
      .then(response => response.json())
      .then(parsedResponse => {
        this.setState({
          someProperty: parsedResponse,
        })
      })
  }

  render(){
    return (
      <div>
        <p>Hello, world!</p>
        <span>{this.state.someProperty}</span>
        {this.someComputedProperty}
      </div>
    )
  }
}

export default SomeComponent
```

## Lifecycle Methods

## Switching a Functional Component to a Class Component

1. Import the `Component` class from the `react` library
2. Change the function declaration to a class declaration that extends `Component`
3. Wrap the JSX `return` value in the `render()` method
4. Destructure any props from `this.props` in the render method
5. Move any `useEffect` hooks into the `componentDidMount` method
6. If needed, move any `useState` hooks into the `state` property, update setter functions to use `setState`, and add `this.state` to any state references

## Switching a Class Component to a Functional Component

1. If needed, import `useState`, switch all `state` values to the `useState` hook, drop `this.state` from all state values, and change all `setState` calls to use the setters from their respective hooks
2. Change the class declaration to a function declaration
3. Remove the `render()` method, leaving the `return` value
4. Destructure any props in the function parameters
5. Move any lifecycle methods into the appropriate hooks
6. Remove the `Component` import

## Watch Out!

* Always use arrow functions for any custom methods you write (method shorthand is preferred for lifecycle methods). This helps keep the `this` value consistent when chaining calls.
* While there are currently no plans to remove class-based components from React, they offer no benefit over functional components and should be avoided.
* It used to be popular to initialize state in the `constructor` method, but this is no longer needed.

## Additional Resources

| Resource | Description |
| --- | --- |
| [React: Official Docs](https://reactjs.org/docs/getting-started.html) | The official (class-based) docs for React |
