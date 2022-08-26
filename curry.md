## Write a curry function that can do the following:

```js
// Modify the below function
function curry(f) {
    // do something
}

// Do not modify the below function
function main() {
    const sum = (a, b) => {
        return a + b;
    };
    const curriedSum = curry(sum);
    curriedSum(1)(2); // returns 3
}
```

Answer

```js
function curry(f) {
    return function(a) {
        return function(b) {
            return f(a, b);
        };
    };
}
```
