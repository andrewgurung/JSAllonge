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
- String, numbers and booleans

```js
// Example: Result of evaluating an expression

2 + 2 === 4
  //=> true

(2 + 2 === 4) === (2 !== 5)
  //=> true
```

### Reference types
- Same type, same content but are not considered identical
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
