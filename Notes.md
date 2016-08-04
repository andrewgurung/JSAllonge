## Values and Expressions
*Note: All values are expressions*

### Values
```js
42
  //=> 42
```
42 is both value and expression

### Expression
```js
"Andrew" + " " + "Gurung"
  //=> Andrew Gurung
```
"Andrew" + " " + "Gurung" is an `expression` made out of string `values` and an `operator`

### Value or Primitive types
- Value types share the same identity if they have the same contents. Considered identical
- String, numbers and booleans

```js
// Example: Result of evaluating an expression

2 + 2 === 4
  //=> true

(2 + 2 === 4) === (2 !== 5)
  //=> true
```

### Reference types
- Reference types do not share the same identity even if they have the same contents
- Objects such as an Array

```js
var a1 = [1,2,3];
var a2 = [1,2,3];
var a3 = [1, 2, 3];
var a4 = [1, 1+1, 2+1];

a1 === a2; // => false
a1 === a3; // => false
a1 === a4; // => false
```

## Numbers

### Floating
- Computer's internal representation of our base 10 literal number is actually in binary.
- Some base 10 fractions do not have exact representation in base 2 notation which leads to error.
- Never use `floating` point numbers to represent monetary amounts

Best Practice:
Use two variables to split fractional amount
```js
var dollars = 43;
var cents = 20;
"$" + dollars + "." + cents; //=> $43.20
```

Traps of floating numbers:
```js
0.1;             //=> 0.1
0.1 + 0.1;       //=> 0.2
0.1 + 0.1 + 0.1; //=> 0.30000000000000004
0.3 + 0.6;       //=> 0.8999999999999999
```
Reference: [Why 0.1 Does Not Exist In Floating-Point](http://www.exploringbinary.com/why-0-point-1-does-not-exist-in-floating-point/)

## Functions

### Simplest possible function
No input values and returns `0`

Note: Though internally JavaScript stores a full and proper function, it returns [Function] or ()=>0 based on JavaScript environment that hosts the JavaScript REPL

```js
() => 0
//=> [Function]       in NodeJS environment
//=> function ()=>0   in Chrome envrionment
//=> ()=>0            in Firefox envrionment
```

### Functions are reference types
Like Arrays, every time you evaluate an expression to produce a function, you get a new function that is not identical to any other function
```js
(()=>0) === (()=>0)
//=> false
```

Applying functions: fn_expression(args)
```js
(()=>0)();
//=> 0

(()=>"Andrew" + " " + "Gurung")();
//=> Andrew Gurung

(()=>1+2)();
//=> 3

(()=>(()=>0)())();
//=> 0
```

### Comma operator
The `comma` operator takes two arguments, evaluates them and returns the value of the right-hand argument

```js
(1, 2); //=> 2
(1+1, 2+2); //=> 4
```

### Block
- A block has zero of more statements, separated by semicolons
- A block can be added to the right of an arrow

```js
(() => {})()
//=> undefined

undefined === undefined
//=> true
```
In JavaScript,
- `undefined` is a value that means "I don't have a value"
- `undefined` is identical to every other `undefined`

### Three ways of generating `undefined` values
1. Evaluating a function that doesn't have value. (()=>{})()
  - Cumbersome
2. By explicitly writing `undefined`
  - `undefined` can be reassigned/mutated
3. By using `void` operator
  - Safe

```js
void 0;       //=> undefined
void 1;       //=> undefined
void (1 + 2); //=> undefined
```
Best Practice: Use `void` to generate `undefined` value

### Statement
- A `block` is a (possibly empty) list of JavaScript statements separated by semicolons
- An `expression` is a JavaScript statement

A block with one or more expressions still evaluates to undefined:
```js
// 1. Single expression will return undefined
(() => { 2 + 3 })(); //=> undefined

// 2. Block with multiple expressions will still return undefined
(() => {
  2 + 3;
  1 + 2;
})(); //=> undefined
```

To return a value when a function is applied/executed, we need the `return` keyword
```js
(() => {
  return 1 + 1;
  2 + 2;
})(); //=> 2
```

Note:
- `return` statement does not behave like an `expression`
- Statements must be inside blocks `{}`
- Other statement examples: Function declaration, for loops, if statements, etc
```js
(() => return 0)();  //=> error
(() => {return 0})();  //=> 0
```

### Function that evaluates to a function
Put an expression that evaluates to a function (Eg: ()=>0) to the right side of a function expression

```js
// 1.
() => () => 0

// 2. Evaluate outer function
(() => () => 0)()
  // Returns:   function () => 0

// 3. Evaluate outer function first and then also evaluate the inner function
(() => () => 0)()()
  // Returns:  0
```

## Arguments

To apply a function with an argument, put it within the parentheses

```js
((radius) => 3.14 * radius * radius)(2); //=> 12.56
```
