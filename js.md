# JavaScript Manual

## Content

- [General info](#Genera_info)

- [Inclusion attributes](#Inclusion_attributes)

- [Variables](#Variables)
- [Variables_Var](#Variables_Var)
- [Variables_Let](#Variables_Let)
- [Variables_Const](#Variables_Const)

- [DataType](#DataType)

- [TypeConversion](#TypeConversion)

- [StatementCicles](#StatementCicles)

- [Function](#Function)
- [Function_Declaration](#Function_Declaration)
- [Function_Expression](#Function_Expression)
- [Function_Anonim](#Function_Anonim)
- [Function_Generator](#Function_Generator)
- [Function_Arrow](#Function_Arrow)
- [Function_Closures](#Function_Closures)
- [MemoizationCaching](#MemoizationCaching)

- [StrictMode](#StrictMode)
- [CallApplyBind](#CallApplyBind)
- [Arguments](#Arguments)

- [Array](#Array)
- [ForEach_Map_Filter](#ForEach_Map_Filter)
- [SpreadSintaxis](#SpreadSintaxis)

- [Object](#Object)
- [ObjectDefine](#ObjectDefine)
- [ObjectProperties](#ObjectProperties)
- [ObjectCopyNew](#ObjectCopyNew)
- [ObjectCallApplyBind](#ObjectCallApplyBind)
- [Context](#Context)

- [ProtoPrototype](#ProtoPrototype)

- [Class](#Class)

- [CallBack](#CallBack)

- [Promise](#Promise)

- [AsyncAwait](#AsyncAwait)

## Genera_info

JS - java script - ECMAScript (European Computer Manufacturers Association) - standart.

## Inclusion_attributes

As rule script include on end Body. </br>
Scripts are executed in order

```jsx
<body>
  {" "}
  <script src="script.js"></script>
  //////////////////////
  <script src="script2.js"></script>
  <script>//////////////////////</script>
</body>
```

Attributes async && defer

```jsx
<body>
  <script defer src="script.js"></script> //run script after full download page
  <script async src="script2.js"></script> //run script async
</body>
```

We can use Module export/import
https://developer.mozilla.org/ru/docs/Web/JavaScript/Guide/Modules

!!New browsers all will GET ERROR (CORS) and won't execute JS script, if we will try launch browser as local (right click on index.html). We can use it only by launch a server (local server).

```jsx
<script type="module" src="./js/index.js" defer></script> //type="module" - is needed!
```

## Variables

https://medium.com/nuances-of-programming/%D0%B2-%D1%87%D1%91%D0%BC-%D1%80%D0%B0%D0%B7%D0%BD%D0%B8%D1%86%D0%B0-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-var-let-%D0%B8-const-%D0%B2-javascript-3084bfe9f7a3

<h2>var, let, const</h2>

JS has 3 area of visibility: global scope, function scope, block scope (all betveen {}). </br>

2 area of visibility for var: global scope и function scope </br>
3 area of visibility for let, const: global scope, function scope, block scope.

### Variables_Var:

Available inside Global Scope and in the function (in which it is declared) and in nested functions (function scope). </br>
Var return "undefined" if it call till get value or declaration:

```jsx
var declaration;
console.log(declaration); // undefined

function discountPrices(prices, discount) {
  var discounted = [];
  for (var i = 0; i < prices.length; i++) {
    var discountedPrice = prices[i] * (1 - discount);
    var finalPrice = Math.round(discountedPrice * 100) / 100;
    discounted.push(finalPrice);
  }
  console.log(discountedPrice); // some value
  return discounted;
}
console.log(discounted); // Reference Error
console.log(x); //undefined
var x = 2;
```

### Variables_Let:

Available inside Global Scope and in the function (in which it is declared) and in nested functions (function scope). Also available inside the block scope (all betveen {}) (in which it is declared) and in nested functions and block{}.</br>
let return ReferenceError if it call till declaration && return undefined if it call till get value:

```jsx
console.log(x);
let x = 2; //ReferenceError
let x2;
console.log(x2); //undefined
```

### Variables_Const:

The same as let, diferent - const value can't reset (for type-value), but can reset field or array element for type-reference (object, array)</br>
const should always be used, except when it need to reset (use let)

```jsx
const x = "wwwww";
x = "rrrr"; // ❌ TypeError: Assignment to constant variable.
const person = {
  name: "Jim",
};
person.name = "Bill"; //Bill
person = {}; // ❌TypeError:redeclaration of const person
const x = [2, 3, 4, 5, 7];
console.log(x); //Array(5) [ 2, 3, 4, 5, 7 ]
x[2] = 33;
console.log(x); // Array(5) [ 2, 3, 33, 5, 7 ]
x = [];
console.log(x); // ❌TypeError:invalid assignment to const 'x'
```

## DataType

https://learn.javascript.ru/types

type-value:</br>
• number //4, 4.32, Infinity, NaN (NaN is calculate Error, NaN != Nan, for check - isNaN())</br>
typeof number //number</br>
• bigint //const bigInt = 1234567890123456789012345678901234567890n;</br>
typeof bigInt; //"bigint"</br>
• string</br>
typeof string //string</br>
• boolean</br>
typeof boolean //boolean</br>
• undefined</br>
typeof undefined //undefined</br>
• null</br>
typeof null //object !!!!!! bug - must be null</br>
• symbol</br>
const sym = Symbol("foo");</br>
typeof sym; // "symbol"</br>

type-reference:</br>
• array</br>
typeof array //object !!!!!!!!!!!!!</br>
• function</br>
typeof function //function</br>
• object</br>
typeof object //object</br>

```jsx
//type-value - we have different instances and i let a and in let b:
let a = 5;
let b = a;
b += 2;
console.log(`a=${a},    b=${b}`); //a=5,    b=7
//type-reference - we have the same object and in const a and in const b:
const a = [1, 2, 3, 4];
const b = a;
b.push(44);
console.log(`a=${a},    b=${b}`); //a=1,2,3,4,44,    b=1,2,3,4,44
```

## TypeConversion

1. number

- mathematical expressions
- сomparison of different types
- function Number(value)
- unary "+" before expression

2. string

- alert()
- function String(str)
- operator "+", if one of the operands is a string

3. bool

- operands if, else, switch
- logical operators (||, &&,!), logical negation !!
- Boolean(value)

## StatementCicles

- [if_else_and_conditional_ternary_operator](#if_else_and_conditional_ternary_operator)
- [switch_operator](#switch_operator)
- [for_statement](#for_statement)
- [do_while_statement](#do_while_statement)
- [while_statement](#while_statement)
- [for_in_statement](#for_in_statement)
- [for_of_statement](#for_of_statement)

### if_else_and_conditional_ternary_operator

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else?retiredLocale=uk </br>
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator?retiredLocale=uk </br>

The if statement executes a statement if a specified condition is truthy. If the condition is falsy, another statement can be executed. </br>

```jsx
//use if...else if...else
const x = 5;
if (x >= 0 && x < 4) {
  console.log(`x = ${x}, this value >= 0 && < 4`);
} else if (x >= 4 && x < 25) {
  console.log(`x = ${x}, this value >= 4 && < 25`); //x = 5, this value >= 4 && < 25
} else {
  console.log(`x = ${x}, this value >= 25`);
}
//conditional (ternary) operator (not necomemd to use!!) as difficult for understand in long code:
const age = 26;
let beverage = age >= 21 ? "Beer" : "Juice";
console.log(`For age ${age} yers old, your favorite beverage is ${beverage}`); // For age 26 yers old, your favorite beverage is Beer
```

### switch_operator

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch </br>

The switch statement evaluates an expression, matching the expression's value to a case clause, and executes statements associated with that case, as well as statements in cases that follow the matching case.

```jsx
const action = "say_hello";
switch (action) {
  case "say_hello":
    let messageHello = "hello";
    console.log(messageHello);
    break;
  case "say_hi":
    let messageHi = "hi";
    console.log(messageHi);
    break;
  default:
    console.log("no action.");
    break;
}
```

### Loops_and_iteration

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration?retiredLocale=uk </br>

#### for_statement

A for loop repeats until a specified condition evaluates to false. The JavaScript for loop is similar to the Java and C for loop. Array.prototype.forEach() should be preferred and "for" only used when necessary.

```jsx
const arr = ["one", "two", "three", "four", "five"];
for (let i = 0; i < arr.length; i++) {
  console.log(`${i} element of array is ${arr[i]}`);
} // 0 element of array is one
// 1 element of array is two
// 2 element of array is three
// 3 element of array is four
// 4 element of array is five
```

We can use "break statement" and "continue statement" in loop "for". Also if we have multiple levels of nesting loop - in this case we cant use "labeled statement" for diferentiation - what loop we must break (continue).

#### do_while_statement

The do...while statement repeats until a specified condition evaluates to false. !! One time the body of the loop do...while will be executed anyway.

```jsx
let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 0); //1 !!

let i = 0;
do {
  i += 1;
  console.log(i);
} while (i < 5); //1 2 3 4 5
```

We can use "break statement" and "continue statement" in loop "do...while". Also if we have multiple levels of nesting loop - in this case we cant use "labeled statement" for diferentiation - what loop we must break (continue).

#### while_statement

A while statement executes its statements as long as a specified condition evaluates to true.

```jsx
let n = 0;
while (n < 0) {
  console.log(n); //undefined !! loop not working
  n++;
}

let n = 0;
while (n < 5) {
  console.log(n); //0 1 2 3 4
  n++;
}
```

We can use "break statement" and "continue statement" in loop "while". Also if we have multiple levels of nesting loop - in this case we cant use "labeled statement" for diferentiation - what loop we must break (continue).

#### for_in_statement

The for...in statement iterates a specified variable over all the enumerable properties of an object. For each distinct property, JavaScript executes the specified statements. (see objects)

```jsx
const book = {
  autor: "Garyson",
  name: "StanleSteelRat",
  yearRelease: 1988,
};
for (const property in book) {
  console.log(`${property}: ${book[property]}`);
}
// autor: Garyson
// name: StanleSteelRat
// yearRelease: 1988
```

We can use "break statement" and "continue statement" in for...in statement.

#### for_of_statement

The for...of statement creates a loop Iterating over iterable objects (including Array, Map, Set, arguments object and so on), invoking a custom iteration hook with statements to be executed for the value of each distinct property.

```jsx
const arr = [3, 5, 7];
for (let i of arr) {
  console.log(i); // logs 3, 5, 7
}
```

We can use "break statement" and "continue statement" in for...of statement.

## Function

https://developer.mozilla.org/ru/docs/Web/JavaScript/Guide/Functions

### Function_Declaration

a function declared in the main code flow (created until code run -- so call function untill its create - work!)

```jsx
function decl(x) {
  return this;
}
//when need to run function now:
(function decl(r) {
  console.log(r);
})(555); //555
```

### Function_Expression

function declaration in the context of some expression, for example assignment (created after code run -- so call function untill its create - not work!)

```jsx
const expr = function (x) {
  return x;
};
```

### Function_Anonim

fubction without name - can be passed as parameter other function

```jsx
const ex = function (x, y) {
  x();
  y();
};

ex(
  function () {
    alert("X");
  },
  function () {
    alert("Y");
  }
);
```

### Function_Generator

```jsx
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}
```

### Function_Arrow

function - always anonim function (without name) not have own "arguments", "super", "new.target". Can't creat objects from arrow functions. "This" for arrow function always bind to envirement, where arrow function was be executed!!! (not created!!) We can't reset "this" for arrow function by use Call, Apply, Bind (as opposed to a function declaration or expression) (for more information see below - Context).

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Arrow_functions </br>

```jsx
// short syntax
const func = (x) => x * x;

// full syntax
const func = (x, y) => {
  return x + y;
};

//common anonim function
elements.map(function (element) {
  return element.length;
});

//arrow function with brackets (){} --full sintax
elements.map((element) => {
  return element.length;
});

//arrow function with brackets (){} and without return --short sintax
elements.map((element) => element.length);
```

### Function_Closures

https://developer.mozilla.org/ru/docs/Web/JavaScript/Guide/Functions#%D0%B7%D0%B0%D0%BC%D1%8B%D0%BA%D0%B0%D0%BD%D0%B8%D1%8F </br>

```jsx
//first case
var pet = function (name) {
  var getName = function () {
    return name;
  };
  return getName;
};
myPet = pet("Vivie");
myPet(); //will return Vivie

//second case
const out = function (count) {
  const ob = {};
  const inn = function () {
    //check is object empty
    if (Object.keys(ob).length === 0) {
      for (let i = 1; i < count; i++) {
        console.log(`${i} call in empty object`);
        ob[i] = i;
      }
    } else {
      let countN = Object.keys(ob).length + count;
      for (let i = count; i < countN; i++) {
        console.log(`${i} call in filled object`);
        ob[i] = i;
      }
    }
    console.log(ob);
  };
  return inn;
};
const ex = out(5);
ex(); //Object { 1: 1, 2: 2, 3: 3, 4: 4 }
ex(); //Object { 1: 1, 2: 2, 3: 3, 4: 4, 5: 5, 6: 6, 7: 7, 8: 8 }
const exX = out(7);
exX(); //Object { 1: 1, 2: 2, 3: 3, 4: 4, 5: 5, 6: 6 }
```

### MemoizationCaching

https://habr.com/ru/company/ruvds/blog/332384/ </br>

Cache - is an intermediate buffer with fast access to it, containing information that can be requested with the highest probability. Accessing data in the cache is faster than fetching the original data from slower memory or a remote source, but its volume is significantly limited compared to the source data store. </br>

Memoization - is an optimization method that is mainly used to speed up computer programs by storing the results of expensive function calls and returning the cached result when calls on the same input data occur again . </br>

```jsx
//this is memoised function
const sample = (x) => {
  let res = x + 5;
  console.log(`result = ${res}`);
  return x + 5;
};
//this is memisation function, we will dispatch memoised function as parameter
const memo = (fn) => {
  cash = {};
  return (...args) => {
    let v = args[0];
    if (v in cash) {
      console.log(`result from cashe = ${cash[v]}`);
      return cash[v];
    } else {
      console.log("result from calculating");
      let result = fn(v);
      cash[v] = result;
      return result;
    }
  };
};
const ex = memo(sample);
ex(5); //result from calculating  result = 10
ex(7); //result from calculating  result = 12
ex(5); //result from cashe = 10
```

## StrictMode

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Strict_mode

## CallApplyBind

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call?retiredLocale=uk

## Arguments

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/arguments

this is array wich content function arguments

```jsx
function func1(a, b, c) {
  console.log(arguments[0]);
  // expected output: 1
}

func1(1, 2, 3);
```

## Array

typeof array //object !!!!!!</br>
array is spesial type of object

```jsx
const w = [1, 2, 3, 4, 5];
w[2] = 55;
console.log(w); //Array(5) [ 1, 2, 55, 4, 5 ]

let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
alert(matrix[1][1]); // 5

//define dinamic multi matrix
const matrixRandom = [];
for (let i = 0; i < sizeMatrix; i++) {
  matrixRandom[i] = [];
}

//copy array
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4);
// arr2 becomes [1, 2, 3, 4]
// arr remains unaffected
```

When to Use Arrays. When to use Objects. </br>

JavaScript does not support associative arrays.
You should use objects when you want the element names to be strings (text).
You should use arrays when you want the element names to be numbers.

## ForEach_Map_Filter

### forEach

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach </br>

The forEach() method executes a provided function once for each array element.

```jsx
const arr = ["a", "b", "c", "d"];
arr.forEach((element) => console.log(element)); //a b c d

const arr = ["a", "b", "c", "d"];
arr.forEach((element, index) =>
  console.log(`${index} array element is ${element}`)
); //0 array element is a
//1 array element is b
//2 array element is c
//3 array element is d
```

### map

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map?retiredLocale=uk </br>

The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.

```jsx
const arr = [1, 3, 5, 8];
const newArr = arr.map((x) => x * 4);
console.log(newArr); //Array(4) [ 4, 12, 20, 32 ]
```

### filter

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter?retiredLocale=uk </br>

The filter() method creates a new array with all elements that pass the test implemented by the provided function. Diferent between filter() vs map() - filter() don't create new elements (just select needed elements); map create new elements.

```jsx
const arr = ["spray", "limit", "elite", "exuberant", "destruction", "present"];
const result = arr.filter((word) => word.length > 6);
console.log(result); //Array(3) [ "exuberant", "destruction", "present" ]

//also we can dispatsh to callback as paremeters: index of current element && fully current array

//dispatch callback to filter
function isBigEnough(value) {
  return value >= 10;
}
const filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
console.log(filtered); //Array(3) [ 12, 130, 44 ]

//returns all prime numbers in an array:
const array = [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
function isPrime(num) {
  for (let i = 2; num > i; i++) {
    if (num % i == 0) {
      return false;
    }
  }
  return num > 1;
}
console.log(array.filter(isPrime)); // [2, 3, 5, 7, 11]

//we can change our source array in callbackFilter - in this case filter will work with new values:
let words = ["spray", "limit", "exuberant", "destruction", "elite", "present"];
const modifiedWords = words.filter((word, index, arr) => {
  arr[index + 1] += " extra";
  return word.length < 6;
});
console.log(modifiedWords); //Array [ "spray" ]

//when we will add new arrayElement in callbackFilter - filter don't see it:
words = ["spray", "limit", "exuberant", "destruction", "elite", "present"];
const appendedWords = words.filter((word, index, arr) => {
  arr.push("new");
  return word.length < 6;
});
console.log(appendedWords); //Array(3) [ "spray", "limit", "elite" ]
console.log(words); //Array(12) [ "spray", "limit", "exuberant", "destruction", "elite", "present", "new", "new", "new", "new", … ]

//when we will delete arrayElements in callbackFilter - filter won't see deleted elements:
words = ["spray", "limit", "exuberant", "destruction", "elite", "present"];
const deleteWords = words.filter((word, index, arr) => {
  arr.pop();
  return word.length < 6;
});
console.log(deleteWords); //Array [ "spray", "limit" ]
```

## SpreadSintaxis

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Spread_syntax

```jsx
function sum(x, y, z) {
  return x + y + z;
}
const numbers = [1, 2, 3];
//we use spread when we want use array element as several funstion argument
console.log(sum(...numbers));
// expected output: 6
//classic we use next sintaxis for that
console.log(sum.apply(null, numbers));
// expected output: 6
```

also we can use spread sintaxis for copi array

```jsx
var arr = [1, 2, 3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4);
// arr2 becomes [1, 2, 3, 4]
// arr remains unaffected
```

## Object

Object is a reference type. Can use for: 1. Save data as Key: Value. 2. OOP </br>
Object have a properties. A property is a "key: value" pair, where the key is a string (also called a "property name"), and the value can be anything.

### ObjectDefine

```jsx
function Book() {
  (this.autor = "Garyson"),
    (this.name = "StanleSteelRat"),
    (this.yearRelease = 1988),
    (this.showInfo = function (arg) {
      console.log(this.name);
    });
}
const book = new Book();
//or
const book = new (function () {
  (this.autor = "Garyson"),
    (this.name = "StanleSteelRat"),
    (this.yearRelease = 1988),
    (this.showInfo = function (arg) {
      console.log(this.name);
    });
})();
//or
const book = new Object();
book.autor = "Garyson";
book.name = "StanleSteelRat";
book.yearRelease = 1988;
book.showInfo = function (arg) {
  console.log(this.name);
};
//or
const book = {
  autor: "Garyson",
  name: "StanleSteelRat",
  yearRelease: 1988,
  showInfo: function (arg) {
    console.log(this.name);
  },
};
```

### ObjectProperties

```jsx
const book = {
  autor: "Garyson",
  name: "StanleSteelRat",
  yearRelease: 1988,
  showInfo: function (arg) {
    console.log(this.name);
  },
};

const prop = "autor";
console.log(book[prop]);
console.log(book["autor"]);
console.log(book.autor);
book.showInfo("argument");

//use for...in for object properties
for (const property in book) {
  console.log(`${property}: ${book[property]}`);
}

//check if properties is
const prop = "name";
if (prop in book) {
  console.log(`object book have propertie ${prop}`);
} else {
  console.log(`object book don't have propertie ${prop}`);
}
```

### ObjectCopyNew

```jsx
const bookCopy = {};
for (const property in book) {
  bookCopy[property] = book[property];
}
//or
const bookCopy = Object.create(book);
```

### ObjectCallApplyBind

```jsx
const bookCall = {
  autor: "London",
  name: "SmokeBelyu",
};

book.showInfo.call(bookCall, "SomeArgument"); //SmokeBelyu
//applay the same as Call - diferent in argumet transmission method
book.showInfo.applay(bookCall, ["SomeArgument"]);

//bind
setTimeout(book.showInfo.bind(bookCall, "SomeArgument"), 1000);
```

## Context

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this</br>
https://medium.com/webbdev/js-a4a9dfed9782</br>

An execution context is, to put it simply, a concept that describes the environment in which JavaScript code is executed. Code is always executed within some context. </br>

ATTENTION!!! In JS any function DON'T HAVE OWN 'THIS'!! 'This' in function (declaration, expression, arrow) mean as function will execute inside environment some object (that mean - our function will use variables from some oblect). There is different between funstion declaration (expretion) and arrow function, when we use "this":</br>

1. For function declaration (expression) "this" use environment, where function was be CREATED!!. We can change context function declaration (expression) by use Call, Apply, Bind.</br>
2. For arrow function "this" use environment, where function was be EXECUTED (RUN)!! Not created!!. We can't change context arrow function by use Call, Apply, Bind.</br>
   See example below (function context). </br>

ATTENTION!! in JS in Global context, deprecated "var x" the same as "this.x". New "let" && "const" - NO!!!! In Function context - "var x" isn't the same as "this.x"!!!

```jsx
//global context
this.a = "a";
var b = "b";
let c = "c";
const d = "d";
console.log(this.a); //a
console.log(this.b); //b
console.log(this.c); //undefined
console.log(this.d); //undefined

//function context
this.v = 77777; //the same as var v
console.log(this.v); //77777 in global context
function context() {
  var v = 55555; //we haven't changed this.v in global context
  console.log(this); //Window
  console.log(this.v); //77777
}
context();
console.log(this.v); //77777 in global context
```

In JS we have 3 possible contexts:</br>

1. Global context (in browser Global context is object Window)

```jsx
console.log(this); //Window
console.log(this === window); // true
a = 37;
console.log(window.a); // 37
this.b = "MDN";
console.log(window.b); // "MDN"
console.log(b); // "MDN"
```

2. Function context:

```jsx
//next case for function declaration IN NO STRICT regime, we have this=Window inside function context (function isn't object!!!!), this.v=77777 (global context) we will change inside function - this.v = 55555.... so is the same value!!
this.v = 77777;
console.log(this.v); //77777 in global context
function context() {
  this.v = 55555; //we have changed this.v in global context
  console.log(this); //Window
  console.log(this.v); //55555
}
context();
console.log(this.v); //55555 in global context

//in strict mode 'this' inside function is undefined (because function don't bind to any object!)
this.v = 77777;
console.log(this.v); //77777 in global context
function context() {
  "use strict";
  this.v = 55555; //Error - 'this' is undefined
  console.log(this);
  console.log(this.v);
}
context();
console.log(this.v);

//for arrow function "use strict" is working right, because arrow function always have 'this' of environment when it be executed (run):
this.v = 77777;
console.log(this.v); //77777 in global context
const context = () => {
  "use strict";
  this.v = 55555; //we have changed this.v in global comtext
  console.log(this); //Window
  console.log(this.v); //55555
};
context();
console.log(this.v); //55555 in global context

//we can change "this" for function declaretion (expression) by use Call, Apply, Bind:
const obj = { a: "Custom" };
this.a = "Global";
function whatsThis() {
  console.log(this.a);
}
whatsThis(); // 'Global'
whatsThis.call(obj); // 'Custom'
whatsThis.apply(obj); // 'Custom'

//we can't change "this" for arrow function by use Call, Apply, Bind:
const obj = { a: "Custom" };
var a = "Global";
const whatsThis = () => {
  console.log(this.a);
};
whatsThis(); // 'Global'
whatsThis.call(obj); // 'Global' - we EXECUTE arrow function in global context
whatsThis.apply(obj); // 'Global' - we EXECUTE arrow function in global context

//if in object where was be created our function missing needed this.value - in that case value will be undefined!
this.a = "global";
const obj = {
  a: "Custom",
  b: function () {
    console.log(this.a);
  },
};
obj.b(); //Custom

this.a = "global";
const obj = {
  b: function () {
    console.log(this.a);
  },
};
obj.b(); //undefined

this.a = "global";
const obj = {
  a: "Custom",
  b: function () {
    const x = () => this.a; //context arrow function - its envirement - function expression inside object obj.
    return x;
  },
};
const fn = obj.b();
console.log(fn()); // Custom

this.a = "global";
const obj = {
  b: function () {
    const x = () => this.a; //context arrow function - its envirement - function expression inside object obj.
    return x;
  },
};
const fn = obj.b();
console.log(fn()); // undefined

//be carefull!! if we just assign fn = obj.b; without Execute - we get other result!! - our function expression b will execute in global context:
this.a = "global";
const obj = {
  b: function () {
    const x = () => this.a; //context arrow function - its envirement - function expression inside object obj.
    return x;
  },
};
const fn = obj.b;
console.log(fn()()); // global
```

3. Eval function execution context

Eval function execution context. Code running inside the eval function also has its own execution context. However, the eval function is rarely used, so we won't talk about this execution context here.

## ProtoPrototype

JS - prototype inheritance language</br>
all function (declaration, expression (not arrow!!)) have propertie "prototype" (Func.prototype = { constructor: function Func() }; //as default)</br>
all object have object-prototype (template from which the object inherits all properties and methods ); this object-prototype can have own object-prototype ect.... (сhane of prototype)</br>
object-prototype (in object) create from function.prototype (propertie function) when doing <const f = new Func();>. After object-prototype and function.prototype independent from each other</br>
we can get function.prototype by means of Func.prototype properties. We can get access to object-prototype by means of \_\_proto\_\_ (deprecated getter/setter for object-prototype) or Object.getPrototypeOf(obj)/Object.setPrototypeOf(obj, prototype)</br>
</br>
https://learn.javascript.ru/function-prototype /////////function prototype f.prototype</br>
https://learn.javascript.ru/prototype-inheritance ///////object prototype [[prototype]]</br>
https://developer.mozilla.org/ru/docs/Learn/JavaScript/Objects/Object_prototypes</br>
</br>
all function have propertie "prototype" = as default { constructor: nameFunction } who refer on function-constructor;</br>

```jsx
function Func() {
  this.prop = "Value";
}
/* prototype as defoult
Func.prototype = { constructor: function Func() };
*/
console.log(Func.prototype.constructor === Func); // true

//we cane change prototype and new object will creat, but of course we can't use Constructor property
Func.prototype = {};
//also we can change prototype (add new property): Func.prototype.newProp = "someValue"
const f = new Func();
console.log(f.prop); //Value
console.log(Func.prototype); //{}

function FuncInherit() {
  this.propInherit = "propInherit";
}
const fInh = new FuncInherit();
console.log(fInh.__proto__); //{ constructor: function FuncInherit() }
console.log(Object.getPrototypeOf(fInh)); //{ constructor: function FuncInherit() }

Func.prototype = FuncInherit.prototype;
console.log(Func.prototype); //{ constructor: function FuncInherit() };
console.log(FuncInherit.prototype); //{ constructor: function FuncInherit() };

const exanpleInh = {
  ex: 555,
};
Object.setPrototypeOf(fInh, exanpleInh); //the same as: fInh.__proto__= exanpleInh;
console.log(fInh.ex); //555
```

## Class

https://learn.javascript.ru/class
https://learn.javascript.ru/es-class

class this is syntactic sugar in js, but with important additions, like: UseStrikt, [[IsClassConstructor]]: true, enumerable-false for all methods (metods don't see on for...in) ect.</br>
class in js haven't Privat && Protected props

```jsx
//class Declaration
class User {
  constructor(name) {
    this.name = name;
  }
  sayHi() {
    console.log(this.name);
  }
}
//or class Expression
const User = class {
  constructor(name) {
    this.name = name;
  }
  sayHi() {
    console.log(this.name);
  }
};

console.log(typeof User); // function

const user = new User("Jim");
user.sayHi(); //Jim

//getterSetterСomputed properties
class User {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  set fullName(newValue) {
    [this.firstName, this.lastName] = newValue.split(" ");
  }
  ["test".toUpperCase()]() {
    console.log("PASSED!");
  }
}
let user = new User("Bill", "Smit");
console.log(user.fullName); // Bill Smit
user.fullName = "Jim London";
console.log(user.fullName); // Jim London
user.TEST(); // PASSED!

//static properties and methods - access without create new object thgrou dot .
class User {
  static prop = "555";
}
console.log(User.prop); //555

//inheritance
class Animal {
  constructor(name) {
    this.name = name;
  }
  walk() {
    alert("I walk: " + this.name);
  }
}

class Dog extends Animal {
  constructor() {
    //this in children constructor need to invoke after declarate super, otherwise Error
    // constructor parent class invoke avto if in children no own constructor, elst need to invoke parent constructor:
    super("Dog"); // the same as  Animal.call(this, "Dog")
  }
  move() {
    //in children we have access to parent's methods thgrou Super
    super.walk();
    alert("...and jump!");
  }
}

new Dog().walk(); // I walk: Dog
alert(Dog.prototype.__proto__ == Animal.prototype); // true
```

## CallBack

https://developer.mozilla.org/ru/docs/Glossary/Callback_function
https://learn.javascript.ru/callbacks

CallBack - is a function passed to another function as an argument, which is then called upon completion of some action

```jsx
//sync callback
function greeting(name) {
  alert("Hello " + name);
}
function processUserInput(callback) {
  var name = prompt("Please enter your name.");
  callback(name);
}
processUserInput(greeting);

//acync callback
async function pageLoader(callback) {
  const data = await fetch("/docs/Glossary/Callback_function");
  callback(data);
}
function onPageLoadingFinished(pageData) {
  console.log("Page was sucessfully loaded!");
  console.log("Response:");
  console.log(pageData);
}
pageLoader(onPageLoadingFinished);

//acync callback with onload && onerror
function loadScript(src, callback) {
  let script = document.createElement("script");
  script.src = src;
  script.onload = () => callback(null, script);
  script.onerror = () => callback(new Error(`Error download script ${src}`));
  document.head.append(script);
}
loadScript("/my/script.js", function (error, script) {
  if (error) {
    // hundle error
  } else {
    // do something
  }
});
```

## Promise

https://learn.javascript.ru/promise-basics </br>
https://learn.javascript.ru/promise-chaining </br>
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise?retiredLocale=uk </br>

The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.</br>
Function in Promise - Executor. Argument of Executor - buildin in JS functions Resolve && Reject (will inwoke in Executor)</br>
Resolve || Reject can only be called once (all next calls will be ignored). Reject always need to call with Error argument.</br>
Functions consumers - function who will call as result complete execute asynchronus operation. This functionConsumers are used by means of metods: then, cath. finally.</br>

```jsx
let mode = true;

let promise = new Promise(function (resolve, reject) {
  if (mode) {
    setTimeout(() => resolve("done"), 1000);
  } else {
    setTimeout(() => reject(new Error("Whoops!")), 1000);
  }
  //next call resolve/reject will be ignored (need to count with asinchronus ! in this case next Error will execute first (setTineout)). Don't do like this)))!
  reject(new Error("…")); // will ignore, but in this case - not!!
  resolve("…"); // will ignore
});
//then
promise.then(
  (result) => {
    console.log(result);
  }, //handle when Resolve is runed
  (error) => {
    console.log(error);
  } // handle when Reject is runed
);
//if we pass only one function - this is handled when Resolve is runed. In case Reject - operation will ending with unhandled Error!!
//if we want handle only Error - we can to use Cath (or pass Null as first function to Then  .then(null, errorHandlingFunction))
promise.catch((error) => {
  console.log(error);
});
//if we want to execute function in any cace (or Resolve or Reject does not matter) - need to use Finally
promise.finally(() => {
  console.log("Stop onload indicator");
});

// chain of handlers (in this case Then will return Promise with Resolve && Value)
new Promise(function (resolve, reject) {
  setTimeout(() => resolve(1), 1000); // (*)
})
  .then(function (result) {
    // (**)
    alert(result); // 1
    return result * 2;
  })
  .then(function (result) {
    // (***)
    alert(result); // 2
    return result * 2;
  })
  .then(function (result) {
    alert(result); // 4
    return result * 2;
  });
```

## AsyncAwait

https://learn.javascript.ru/async-await

AsyncAwait - sintaxis for work with promises.</br>
Async function always return promise. As default (Resolve promise):

```jsx
async function f() {
  return 1;
}
f().then(alert); // 1
```

or we can return a promise explicitly:

```jsx
async function f() {
  return Promise.resolve(1);
}
f().then(alert); // 1
//or
async function f() {
  return Promise.reject(55555);
}
f().then(null, (w) => console.log(w)); // 5555
//f().catch((w)=>console.log(w)); // 5555
```

Word AWAIT we can to use only in Async function. Await will make the JavaScript interpreter wait until the Promise on right is executed

```jsx
async function f() {
  let promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Done!"), 1000);
  });
  let result = await promise; // will wait until promise on right is execute

  alert(result); // "Done!"
}

f();
```
