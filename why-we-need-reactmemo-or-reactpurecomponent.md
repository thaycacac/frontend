# Why we need React.memo or React.PureComponent?

When props within a React functional component change, the whole component rerenders by default. To put it in another way, if a value inside the component changes, the entire component will rerender, along with all the functions or components whose values or props haven’t changed.

This will result in a performance pitfall, which can be avoided with memoization.

Both functional and class components benefit from memoization. React offers HOCs and hooks to implement this feature. We can use `React.PureComponent` within class components. Memoization for functional components is also possible with `React.memo()` HOC and `useMemo()` Hook. The `useCallback()` Hook is also there for caching functions instead of values.

## PureComponent

`React.PureComponent` helps us to implement memoization in a class component. PureComponent implements `React.ShouldComponentUpdate()`, which performs a shallow comparison of state and props and only renders the React component if the props or state have changed.

In this case, we have to keep the props and state as simple as possible. Since PureComponent may yield incorrect results if they include any advanced data structures. As PureComponent’s `shouldComponentUpdate()` avoids prop updates for the entire component subtree, we should also ensure that all PureComponent’s children are also PureComponent.

## React.memo()

`React.memo()` is very simple to use because it is identical to `React.PureComponent`. While `React.memo()` works with functional components, PureComponent works with class components.

# How about useCallback and useMemo?

## useMemo()

In React, the `useMemo()` hook is the most fundamental method of memoization. You can use `useMemo()` to implement memoization if you’re a Hooks lover.

To use `useMemo()`, pass a function that performs the heavy computation you want to memoize as the first parameter and an array of all dependencies for that memoization as the second argument. `useMemo()` boosts performance by recalculating the memoized value only if one of the given dependencies changes.

This optimization helps to avoid expensive calculations on every render.

```js
const memoizedValue = useMemo(() =>
   expensiveComputation(a, b), [a, b]
)
```
Let’s consider a simple example for calculating a factorial. When the component renders initially, the useMemo Hook calls FactorialCalc and memoizes the value calculated before returning the result to the component. The significant point here is that if the list of dependencies (`[number]`) we provide does not update between renders, useMemo will return the memoizedFactorial instead of calling FactorialCalc.

```react
import { useState, useMemo } from "react";
const App = () => {
  const [number, SetNumber] = useState(1);
  const memoizedFactorial = useMemo(() => FactorialCalc(number), [number]);
   
  const onChange = (e) => {
     console.log(e.target.value);
     SetNumber(Number(e.target.value));
};
return (
  <div><input type="text" onChange={onChange} />
     {memoizedFactorial}
  </div>
);
};
function FactorialCalc(n) {
  console.log('factorialOf(n) called!');
  return n <= 0 ? 1 : n * FactorialCalc(n - 1);
}
export default App;
```

## useCallback()

`useCallback()` is almost equivalent to `useMemo()` in that it memoizes a result relying on an array of dependencies. However, `useCallback()` is only used for memoizing functions rather than values.

When we used the `React.memo()` in the child component in the previous case, the Child component did not rerender, although the Parent component did. Nevertheless, passing a function as a prop to a Child component would still cause the Child component to rerender, even with `React.memo()`.

Consider the following example.

```js
//Parent.js
export default function Parent() {
  const [counter, setCounter] = useState(0);
  const handleClick = () => {
      setCounter(counter + 1);
};

const onClick= () => {
  console.log("onClick");    
  // This is the new handler that will be passed to the child
};

console.log("Parent render");
  return (
    <div className="App"><button onClick={handleClick}>Increase</button><h2>{counter}</h2><Child name={"child"} childHandler={onClick} /></div>
  );
}
```

And the Child component will look like this.

```js
//Child.js
export function Child(props) {
  console.log("Child render");
  return (
     <div><h2>{props.name}</h2></div>
  );
}

export default React.memo(Child);
```

The useCallback helps us to prevent recreating the method each time the parent component is rendered. We have to introduce the `useCallback()` Hook to the onClick function in this case. We can use an empty, a single, or a list of dependencies as the second argument. A memoized result of the callback provided as the first argument is returned if the dependencies specified in useCallback() do not update.

Even when the props provided haven’t changed, when we increase the counter in the Parent component, it rerenders the Child component, as well.

So, what triggers the Child component to rerender is that a new onClick function is generated and sent to the Child component each time the Parent component rerenders. Because the onClick function is created with each rerender, the Child detects that the onClick reference has updated and rerenders the Child component solely on a basic comparison of props.

The `useCallback` helps us to prevent recreating the method each time the parent component is rendered. We have to introduce the `useCallback()` Hook to the onClick function in this case. We can use an empty, a single, or a list of dependencies as the second argument. A memoized result of the callback provided as the first argument is returned if the dependencies specified in `useCallback()` do not update.

```js
//Parent.js
export default function Parent() {
 const [counter, setCounter] = useState(0);
 const handleClick = () => {
   setCounter(counter + 1);
 };

 const onClick= useCallback(() => { //using useCallback() for the handler function
    console.log("handler");
 }, []);

 console.log("Parent render");
   return (
     <div className="App"><button onClick={handleClick}>Increase</button><h2>{counter}</h2><Child name={"joe"} childHandler={onClick} /></div>
   );
}
```

The Child component won’t change.

As we used the `useCallback()` Hook for the Parent `onClick`, it will not be created for each Parent rerender, and a memoized instance of the onClick will be passed down to the Child.
