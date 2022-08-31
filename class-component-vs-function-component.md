# Functional Components vs Class Components

|Functional Components|Class Components|
|---------------------|----------------|
|A functional component is just a plain JavaScript pure function that accepts props as an argument and returns a React element(JSX).| A class component requires you to extend from React. Component and create a render function which returns a React element.|
|There is no render method used in functional components.|It must have the render() method returning JSX (which is syntactically similar to HTML)|
|Functional component run from top to bottom and once the function is returned it cant be kept alive.| Class component is instantiated and different life cycle method is kept alive and being run and invoked depending on phase of class component.|
|Also known as Stateless components as they simply accept data and display them in some form, that they are mainly responsible for rendering UI.|Also known as Stateful components because they implement logic and state.|
|React lifecycle methods (for example, componentDidMount) cannot be used in functional components.|React lifecycle methods can be used inside class components (for example, componentDidMount).|
|Hooks can be easily used in functional components to make them Stateful. example: `const [name,SetName]= React.useState(‘ ‘)` | It requires different syntax inside a class component to implement hooks. example: `constructor(props) { super(props); this.state = {name: ‘ ‘}}`|

## When to use the Class Component and the Functional Component?

To answer this question we need to have a decent understanding of the state of the component.

To recall or revise the concept of the state of the component, I suggest you refer to [this](https://reactjs.org/docs/state-and-lifecycle.html#gatsby-focus-wrapper).

In class components, the render method will be called, whenever the state of the components changes. On the other hand, the Functional components render the UI based on the props.

Whenever we have the use case with the State of the component and rendering the UI based on the Component State, use the Class Components

Class Components should be preferred whenever we have the requirement with the state of the component.

In the beginner stage of the developer journey, we should be familiar with the Class Components and the Functional Components, As we progress towards the Advanced stage of our developer journey, We are able to understand much more cool stuff provided by React like Hooks

In React version > 16.8, React even facilitates developers with Hooks to use the state and other React features even without writing the Class Component
