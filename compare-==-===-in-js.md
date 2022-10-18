|== (Double Equals)|	=== (Triple Equals)|
|------|-------|
|It is used to compare the variables or values|	It is also used to compare the variables/values|
|Doble equals do not check the data type of variable/value while the comparison|	Triple Equals checks the data type of a variable while the comparison|
|Use this when you are unsure about the data type of variable/values|	Use this when you sure about the data type of variable/values and want strict comparison.|
|'1' == 1 This will return true because double equals don’t check the data type.|	'1' === 1 This will return false because triple equals compare the data type too. Simply string is not a number|
|0 == false It will return true because double equals convert the 0 to false and then compared|	0 === false It will return false because they are of a different type|
|7 == "7" // true|	7 === "7" // false|
|7 == 7 // true|	7 === 7 // true|
