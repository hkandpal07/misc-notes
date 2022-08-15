- **ReactDOM.render():** Renders your component to a target element: ReactDOM.render(<MyComponent />, document.getElementById('app'));

- **What is JSX:** Javascript XML. It's Javascript written as HTML. Syntax provided by React to write UI elements using Javascript.

- **Components and extends React.Component:** React.Component is a class that you can inherit to make your class components. Class Components maintain their own states. Functional components are usually stateless but can maintain states using hooks. Components return a JSX. Class components will have a render method defined that will return a JSX. Functional component will simply have this return statement as returning JSX.

- **Nested Components:** Components can be returned by another component.

- **Props and State (props vs state):** 
	- Props are data values that are passed to a component by its parent. State is the data the component maintains internally. 
	- A component can alter its own state, but cannot alter the props passed to it. A parent can however makes changes to the passed props to a child, causing changes. 
	- Changes in both Props and State causes a component to re-renders. 
	- Props can only flow from Parent to child. If you wish to pass data from child to parent then you need to pass a function to the child with appropriate params, and call the function in the child
- **Default Props**: After creating a component, you can have its default props set by creating an object on it as MyComponent.defaultProps = {}. This allows your component to have some default props you expect, if the parent doesn't pass those props.

- **Lifecycle Methods**: Class based components have lifecycle methods that get called during different stages of its lifecycle (mounting, updating, unmounting  etc). Following are a few examples
	- _**ComponentWillMount**_: Called before a component is about to be mounted.
	- _**ComponentDidMount**_: Called after a component is mounted.
	- _**ComponentDidUpdate**_: Called each time a component is updated.
	- _**ComponentWillUnmount**_: Called when a component is about to be unmounted.
	- Even `render` and `constructor` are lifecycle methods that are called in a components lifecycle. Infact `constructor` is called during mounting phase, while `render` is called during mounting as well as update phase.

- **Thinking in React**