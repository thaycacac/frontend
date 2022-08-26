## Implement “Array.reduce” function

```js
function reducer(array, callback, initializer) {
  let accumulator = (initializer === undefined) ? 0 : initializer;

  for (let i = 0; i < array.length; i++) {
    accumulator = callback(accumulator, array[i]);
  }

  return accumulator;
}

const arr = [2, 3, 4];

const sum = (a, b) => a + b;

console.log(reducer(arr, sum, 1)); // logs 10
```
