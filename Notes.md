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
```

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
