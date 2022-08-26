## Implement “debounce” function

```js
function debounce(func, timeout = 300){
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => { func.apply(this, args); }, timeout);
  };
}
function saveInput(){
  console.log('Saving data');
}
const processChange = debounce(() => saveInput());
```

The debounce is a special function that handles two tasks:

- Allocating a scope for the timer variable
- Scheduling your function to be triggered at a specific time

Let’s explain how this works in the first use case with text input.

When a visitor writes the first letter and releases the key, the debounce first resets the timer with `clearTimeout(timer)`. At this point, the step is not necessary as there is nothing scheduled yet. Then it schedules the provided function— saveInput()`—to be invoked in 300 ms.

But let's say that the visitor keeps writing, so each key release triggers the debounce again. Every invocation needs to reset the timer, or, in other words, cancel the previous plans with `saveInput()`, and reschedule it for a new time—300 ms in the future. This goes on as long as the visitor keeps hitting the keys under 300 ms.

The last schedule won’t get cleared, so the `saveInput()` will finally be called.
