## Difference Between Promise and Async/Await

|No|Promise|Async/Await|
|--|-------|-----------|
|1|Promise is an object representing intermediate state of operation which is guaranteed to complete its execution at some point in future.|Async/Await is a syntactic sugar for promises, a wrapper making the code execute more synchronously.|
|2|Promise has 3 states – resolved, rejected and pending.|It does not have any states. It returns a promise either resolved or rejected.|
|3|If the function “fxn1” is to executed after the promise, then promise.then(fxn1) continues execution of the current function after adding the fxn1 call to the callback chain.|If the function “fxn1” is to executed after await, then await X() suspends execution of the current function and then fxn1 is executed.|
|4|Error handling is done using .then() and .catch() methods.|Error handling is done using .try() and .catch() methods.|
|5|Promise chains can become difficult to understand sometimes.|Using Async/Await makes it easier to read and understand the flow of the program as compared to promise chains. |
