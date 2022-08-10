# setTimeout() vs setInterval() Comparison Table

|setTimeout | setInterval|
|-----------|------------|
|This is a time event function used to call another function after a certain time period, but it executes the function only once.	|SetInterval function is the same as setTimeout with a slight difference. Here the setInterval function calls a function after a specific time period, but the execution occurs continuously according to the specified time interval. Here the time interval works like a time gap after which the function has to call the another function every time.|
|The setTimeout function calls the required block of code only once.	|The setInterval function calls the required code after the particular time interval provided, again and again.|
|For clearing the timeout function, one has to use cleartimeout().	|For clearing the setInterval function, one has to use clearInterval().|
|Syntax: setTimeout(<function name>, time in milliseconds) | Syntax: setInterval(<function name>, time in milliseconds)|
