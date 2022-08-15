## ES5
Some important features of ES5.

- "use strict"
- String[number] access
- Multiline strings
- String.trim()
- Array.isArray()
- Array forEach()
- Array map()
- Array filter()
- Array reduce()
- Array reduceRight()
- Array every()
- Array some()
- Array indexOf()
- Array lastIndexOf()
- JSON.parse()
- JSON.stringify()
- Date.now()
- Date toISOString()
- Date toJSON()
- Property getters and setters
- Reserved words as property names
- Object methods
- Object defineProperty()
- Function bind()
- Trailing commas

## ES6 — ECMAScript 2015

Some important features of ES6.

- The let keyword
- The const keyword
- Arrow Functions
- For/of
- Map Objects
- Set Objects
- Classes
- Promises
- Symbol
- Default Parameters
- Function Rest Parameter
- String.includes()
- String.startsWith()
- String.endsWith()
- Array.from()
- Array keys()
- Array find()
- Array findIndex()
- New Math Methods
- New Number Properties
- New Number Methods
- New Global Methods
- Object entries
- JavaScript Modules

[Readmore](http://es6-features.org/)

## ES7 — ECMAScript 2016

ES2016 includes new features

- JavaScript Exponentiation (**)
- JavaScript Exponentiation assignment (**=)
- JavaScript Array.prototype.includes

## ES8 — ECMAScript 2017

7. The key highlight of ES8 was the addition of async functions. Here is the list of new features in ES8

- `Object.values()` and `Object.entries()`
- `String padding` i.e. String.prototype.padEnd() and String.prototype.padStart()
- `Object.getOwnPropertyDescriptors`
- Trailing commas in function parameter lists and calls
- Async functions

## What is profill

New language features may include not only syntax constructs and operators, but also built-in functions.

For example, `Math.trunc(n)` is a function that “cuts off” the decimal part of a number, e.g `Math.trunc(1.23)` returns `1`.

In some (very outdated) JavaScript engines, there’s no `Math.trunc`, so such code will `fail`.

As we’re talking about new functions, not syntax changes, there’s no need to transpile anything here. We just need to declare the missing function.

A script that updates/adds new functions is called “polyfill”. It “fills in” the gap and adds missing implementations.

