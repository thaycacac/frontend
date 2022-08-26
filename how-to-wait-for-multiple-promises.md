## How to wait for multiple promises?

You use `Promise.all()`

```js
const promise1 = //...
const promise2 = //...

const data = await Promise.all([promise1, promise2])

const dataFromPromise1 = data[0]
const dataFromPromise2 = data[1]
```

If you prefer using pure promises and not async/await, use this syntax:

```js
const promise1 = //...
const promise2 = //...

Promise.all([promise1, promise2]).then(data => {
	const dataFromPromise1 = data[0]
	const dataFromPromise2 = data[1]
})
```
