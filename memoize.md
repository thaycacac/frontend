## Write a function that can memoize the result of a function:

```js
// Modify the below function
function memoize(func) {
    // do something
}

// Do not modify the below function
function main() {
    const func = (a, b) => {
        console.log('Doing some calculation');
        return a + b;
    };
    const memoized = memoize(func);
    memoized(1, 2); // returns 3
    memoized(1, 2); // returns 3 (from cache)
    memoized(1, 3); // returns 4
    memoized(1, 3); // returns 4 (from cache)
}
```

Answer

```js
function memoize(func) {
    const cache = {};
    return function(...args) {
        if (cache[args]) {
            return cache[args];
        }
        const result = func(...args);
        cache[args] = result;
        return result;
    }
}

```
