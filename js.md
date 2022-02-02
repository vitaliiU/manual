# JavaScript Manual

## Content

- [General info](##Genera_info)

- [Inclusion attributes](##Inclusion_attributes)

- [Variables](##Variables)
- [Variables_Var](###Variables_Var)
- [Variables_Let](###Variables_Let)
- [Variables_Const](###Variables_Const)

- [DataType](##DataType)

- [TypeConversion](##TypeConversion)

- [Function](##Function)
- [Function_Declaration](###Function_Declaration)
- [Function_Expression](###Function_Expression)
- [Function_Anonim](###Function_Anonim)
- [Function_Generator](###Function_Generator)
- [Function_Arrow](###Function_Arrow)
- [Function_Closures](###Function_Closures)

- [StrictMode](##StrictMode)
- [CallApply](##CallApply)
- [Arguments](##Arguments)

- [Array](##Array)

- [SpreadSintaxis](##SpreadSintaxis)

- [Object](##Object)
- [ObjectDefine](###ObjectDefine)
- [ObjectPropertiesFunction](###ObjectPropertiesFunction)
- [ObjectCopyNew](###ObjectCopyNew)
- [ObjectCallApplyBind](###ObjectCallApplyBind)

- [ProtoPrototype](###ProtoPrototype)

- [Class](##Class)

- [CallBack](##CallBack)

- [Promise](##Promise)

- [AsyncAwait](##AsyncAwait)

## Genera_info

JS - java script - ECMAScript (European Computer Manufacturers Association) - standart. 

## Inclusion_attributes

as rule script include on end Body</br>
scripts are executed in order

```jsx
<body>
  {" "}
  <script src="script.js"></script>
  //////////////////////
  <script src="script2.js"></script>
  <script>//////////////////////</script>
</body>
```

attributes async && defer

```jsx
<body>
  <script defer src="script.js"></script> #run script after full download page
  <script async src="script2.js"></script> #run script async
</body>
```

## Variables

https://medium.com/nuances-of-programming/%D0%B2-%D1%87%D1%91%D0%BC-%D1%80%D0%B0%D0%B7%D0%BD%D0%B8%D1%86%D0%B0-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-var-let-%D0%B8-const-%D0%B2-javascript-3084bfe9f7a3

<h2>var, let, const</h2>

JS has 2 area of visibility: global scope и function scope

### Variables_Var:

available inside the function (in which it is declared) and in nested functions:</br>
var return "undefined" if it call till get value or declaration:

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

available inside the block (all betveen {}) (in which it is declared) and in nested functions and block{}.</br>
let return ReferenceError if it call till declaration && return undefined if it call till get value:

```jsx
console.log(x);
let x = 2; //ReferenceError
let x2;
console.log(x2); //undefined
```

### Variables_Const:

the same as let, diferent - const value can't reset (for type-value), but can reset field or array element for type-reference (object, array)</br>
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
const bigInt = 1234567890123456789012345678901234567890n;</br>
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
   const a = [1, 2, 3, 4];
   const b = a;
   b.push(44);
   console.log(`a=${a},    b=${b}`);
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

function - always anonim function (without name) not have own "this", "arguments", "super", "new.target"
use outer "this". Can't creat objects from arrow functions.

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Arrow_functions

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

https://developer.mozilla.org/ru/docs/Web/JavaScript/Guide/Functions#%D0%B7%D0%B0%D0%BC%D1%8B%D0%BA%D0%B0%D0%BD%D0%B8%D1%8F

```jsx
var pet = function (name) {
  var getName = function () {
    return name;
  };
  return getName;
};
myPet = pet("Vivie");
myPet(); //will return Vivie
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

typeof array //object !!!!!!!!!!!!! #array is spesial type of object

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
const matrixRandom=[];
for(let i=0;i<sizeMatrix;i++){
    matrixRandom[i]=[];
}
}
```

When to Use Arrays. When to use Objects.

JavaScript does not support associative arrays.
You should use objects when you want the element names to be strings (text).
You should use arrays when you want the element names to be numbers.

## SpreadSintaxis

https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Spread_syntax

## Object

Object is a reference type. Can use for: 1. Save data as Key: Value. 2. OOP

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

### ObjectPropertiesFunction

```jsx
const prop = "autor";
console.log(book[prop]);
console.log(book["autor"]);
console.log(book.autor);
book.showInfo("argument");

for (const property in book) {
  console.log(`${property}: ${book[property]}`);
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

## ProtoPrototype

JS - prototype inheritance language
all function (declaration, expression (not arrow!!)) have propertie "prototype" (Func.prototype = { constructor: function Func() }; //as default)
all object have object-prototype (template from which the object inherits all properties and methods ); this object-prototype can have own object-prototype ect.... (сhane of prototype)
object-prototype (in object) create from function.prototype (propertie function) when doing <const f = new Func();>. After object-prototype and function.prototype independent from each other
we can get function.prototype by means of Func.prototype properties. We can get access to object-prototype by means of \_\_proto\_\_ (deprecated getter/setter for object-prototype) or Object.getPrototypeOf(obj)/Object.setPrototypeOf(obj, prototype)

https://learn.javascript.ru/function-prototype /////////function prototype f.prototype
https://learn.javascript.ru/prototype-inheritance ///////object prototype [[prototype]]
https://developer.mozilla.org/ru/docs/Learn/JavaScript/Objects/Object_prototypes

all function have propertie "prototype" = as default { constructor: nameFunction } who refer on function-constructor;

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

class this is syntactic sugar in js, but with important additions, like: UseStrikt, [[IsClassConstructor]]: true, enumerable-false for all methods (metods don't see on for...in) ect.
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

https://learn.javascript.ru/promise-basics
https://learn.javascript.ru/promise-chaining
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise?retiredLocale=uk

The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.
Function in Promise - Executor. Argument of Executor - buildin in JS functions Resolve && Reject (will inwoke in Executor)
Resolve || Reject can only be called once (all next calls will be ignored). Reject always need to call with Error argument.
Functions consumers - function who will call as result complete execute asynchronus operation. This functionConsumers are used by means of metods: then, cath. finally.

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

AsyncAwait - sintaxis for work with promises.
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
