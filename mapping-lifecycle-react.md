You can take advantage of the `useEffec`t hook to achieve the same results as with the `componentDidMount`, `componentDidUpdate` and `componentWillUnmount` methods. `useEffect` accepts two parameters. The first one is a callback which runs after render, much like in `componentDidMount`. The second parameter is the effect dependency array. If you want to run it on mount and unmount only, pass an empty array `[]`.

To clean up, return the callback in useEffect:

```jsx
useEffect(
  () => {
    document.addEventListener(“click”, someFunc);
    
    return () => {
      document.removeEventListener(“click”, someFunc);
    };
  },
  []
);
```

If you want it to behave like `componentDidUpdate`, put some dependencies into the array or don’t pass the second argument at all.

