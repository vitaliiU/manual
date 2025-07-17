# PythonManual

## Content

- [Generalinfo](#Genera_info)
- [PythonInstall](#PythonInstall)
- [PythonInterpreter](#PythonInterpreter)
- [CommonRules](#CommonRules)
- [BuiltInTypes](#BuiltInTypes)

////////////////////////////////////////////////////////////////////////////

- [DataTypeVariables](#DataTypeVariables)
- [References](#References)
- [RequireInclude](#RequireInclude)
- [Function](#Function)
- [Array](#Array)
- [Class_Object](#Class_Object)
- [SQL](#SQL)
- [DRY_YAGNI_KISS_SOLID](#DRY_YAGNI_KISS_SOLID)
- [UML](#UML)
- [Patterns](#Patterns)
- [MVC](#MVC)

- [LARAVEL](#LARAVEL)
- [Middleware](#Middleware)
- [ContractsHelpers](#ContractsHelpers)
- [ServiceContainer](#ServiceContainer)
- [ServiceProviders](#ServiceProviders)
/////////////////////////////////////////////////////////////////////////

## Genera_info

Python is an easy to learn, powerful programming language. It has efficient high-level data structures and a simple but effective approach to object-oriented programming. Python’s elegant syntax and dynamic typing, together with its interpreted nature, make it an ideal language for scripting and rapid application development in many areas on most platforms.</br>
https://www.python.org/</br>
https://docs.python.org/3.14/</br>
https://docs.python.org/3.14/tutorial/index.html</br></br>

online compile Python</br>
https://www.online-python.com/</br>


## PythonInstall
https://wiki.python.org/moin/BeginnersGuide/Download

```shell
// Debian or Ubuntu

$ apt-get install python3 python3-dev
```

## PythonInterpreter
//from terminal (not convinient):
https://docs.python.org/3/tutorial/interpreter.html


```shell
$ cd /usr/local/bin
$ python3.12

// then need enter code step by step each line .... what not convinient, slow and suitable only for simple tasks....
// better use online compile as example https://www.online-python.com/ ( there we can past bloks of code )

// CtrZ - exit
```

## CommonRules

// for Python don't need use any tags (like <?php> etc)

//simple examples: 

```python
# this is comments

#simple arithmetic:
print(2+2)  #=4
print(50 - 5*6)  #=20
print(50 - 5*6) / 4)  #=5.0 (division always returns a floating-point number)

print(17 // 3)  #=5 (floor division discards the fractional part)
print(17 % 3)  #=2 (the % operator returns the remainder of the division)
print(5 ** 2)  #=25 (5 squared (or the same - 5 to the power of 2))
print(2 ** 7)  #=128 (2 to the power of 7)
print(round(22.344678, 2))  #=22.34
print(round(22.345678, 2))  #=22.35

####
x = 4
y = 8
print(x * y) #=32
####
x 
print(x) # ERROR - name 'x' is not defined
####
# last printed expression is assigned to the variable "_" only in Interpreter, in Scrip it need explicitly assigned (what is FOOL in script):
x = 4
y = 8
print(x * y) #=32
print(_+5) #Error - name '_' is not defined
_=x * y
print(_+5) #37
####

#TEXT      https://docs.python.org/3.14/library/stdtypes.html#str 
#Textual data in Python is handled with str objects, or strings. 
#we can't change string value - this impossible (as and in other langueges as rule). Need only create new string.
#we can use: '_' || "_" || '''_''' || """_"""

print('doesn\'t')          #doesn't
print('C:\some\name')      #C:\some
                           #ame
print(r'C:\some\name')     #C:\some\name

print("doesn't")           #doesn't
print("C:\some\name")      #C:\some
                           #ame
print(r"C:\some\name")     #C:\some\name

#'''_''' || """_""" we use for multiple lines (\ can be use for delete empty lines before text)
print("""\                 #first
     first                 #    -second  
         -second
""")

#concatenate
prefix="py"
print(prefix+"thon")       #python

#string as array
s="python"
print(s[0], s[4])       #p o
#we can use even "-" indexes (as example s[-1] what mean s[5] in this case) but this marasmus maybe!!
#slice
print(s[4:6], s[2:], s[:2])       #on thon py
#length
print(len(s))       #6
####

#LIST - in python the same Array
# Lists might contain items of different types, but usually the items all have the same type.
# As and Array, List in python - this is ReferenceType (this mean when we do: newLIst = oldList - in this case and newLIst and oldList - this is the same Object)

ex = [1, 2, 3, 4, 5]
print(ex)                        #[1, 2, 3, 4, 5]
print(ex[1])                     #2
#list is mutable data type
ex[1]=22
print(ex[1])                     #22
print(len(ex))                   #5
```
## BuiltInTypes





//////////////////////////////////////////////////////////////////////////////////////////


## DataTypeVariables

In PHP we have variables ($v) and constats (const). Constants recomend to name only UpperCase (conct WWWWW).

- [CheckVariableExist](#CheckVariableExist)
- [TypeConversion](#TypeConversion)
- [4scalarType](#4scalarType)
- [TwoCombinedTypes](#TwoCombinedTypes)
- [SpetialTypes](#SpetialTypes)
- [PseudoTypes](#PseudoTypes)
- [SuperglobalVariable](#SuperglobalVariable)
- [PredefinedConstants](#PredefinedConstants)
- [ErrorMessageConstants](#ErrorMessageConstants)
- [MagicConstants](#MagicConstants)

### CheckVariableExist

```php
$txt = "PHP";
if (isset($txt) && !empty(txt)){
echo "I love $txt!";
}else{echo "YO!";}
```

### TypeConversion

PHP does not require (or support) an explicit type definition in a variable declaration.
The type of a variable is determined by the context in which the variable is used.

```php
$foo = "0"; // $foo is string
$foo += 2; // $foo is now an integer (2)
$foo = $foo + 1.4; // $foo is now a float (3.4)
$foo = 2 + "10 students"; // $foo is integer (12)
$foo = 4 + "10.2 Points"; // $foo is float (14.2)
```

### 4scalarType

4 scalarType: int, double(float, real), bool, string </br>
also in PHP is NAN (as and in JS NAN we can't compare with anythings!! Check NAN: var_dump(is_nan()). https://www.php.net/manual/ru/function.is-nan.php </br>
All 4 Scalar Types is Types-Values.</br>

```php
//1. int
$v=55;
echo gettype($v); //integer

//2. double(float, real)
//https://www.php.net/manual/ru/language.types.float.php
$v=55.55;
echo gettype($v); //double

//for double(float, real) on php are some BAGS!!!!! Not compare this!!!!
$x = 8 - 6.4; // which is equal to 1.6
$y = 1.6;
var_dump($x == $y); // is not true (false)
echo (int) ((0.1 + 0.7) * 10); // (7 instead of 8)

//3. bool
$v=true;
echo gettype($v); //boolean

//4. string
$v="someText";
echo gettype($v);//string

//for string we can use: single quotes, double quotes, herodoc, nowdoc:

//4.1. single quotes
//for single quotes - escape sequence && variable NOT WORK (work for double quotes and herodok)
$txt = "PHP";
echo 'I love $txt!'; //I love $txt!
echo 'I love \n !! PHP!'; //I love \n !! PHP!

//4.2. double quotes
$txt = "PHP";
echo "I love $txt!"; //I love $txt!
echo "I love \n !! PHP!"; //I love
                        // !! PHP!

//escape sequence for string:
//  \n line translation
//  \r carriage return
//  \t horizontal tab
//  \v vertical tab
//  \\  backslash
//  \$ dollar sign
//  \" double quote

//4.3 herodoc
$name = 'Andy';
echo <<<EOT
My name is "$name".
Now, i'm learning PHP.
EOT; //My name is "Andy". Now, i'm learning PHP.

//4.4 nowdoc
$name = 'Andy';
echo <<<'EOT'
My name is "$name".  Now, i'm learning PHP.
EOT; //My name is Andy. Now, i'm learning PHP.
//!!! nowdoc some envirement can't use!!

//5. NAN
$nan = acos(8);
var_dump($nan, is_nan($nan));//float(NAN) bool(true)

$nan = "text";
var_dump($nan, is_nan($nan));//string(4) "text" NULL

$nan = 55;
var_dump($nan, is_nan($nan));//int(55) bool(false)

$nan = 55.55;
var_dump($nan, is_nan($nan));//float(55.55) bool(false)

$nan = true;
var_dump($nan, is_nan($nan));//bool(true) bool(false)

```

All 4 Scalar Types is Types-Values:

```php
$name = 'Andy';
echo "$name  ";//Andy
$nameChange = $name;
$nameChange = 'Bill';
echo "$name  ";//Andy
echo "$nameChange  ";//Bill
```

### TwoCombinedTypes

2 Combined types (): array and object </br>
Array is a Types-Values, object - is Reference Type.

```php
//array
$array = array(
"foo" => "bar",
"bar" => "foo",
);
// short (from PHP 5.4)
$array = [
"foo" => "bar",
"bar" => "foo",
];
var_dump($array);//array(2) { ["firstKey"]=> string(3) "one" ["secondKey"]=> string(3) "two" }
//!!unlike JS - on PHP we CAN use array as Key=>Value

//object
class Foo
{
public function doFoo()
{
echo "Doing foo.";
}
}
$bar = new Foo;
$bar->doFoo();//Doing foo.
```

Array is a Types-Values, object - is Reference Type.

```php
//Array is a Types-Values
$arrayBase = ['one','two','three'];
var_dump($arrayBase);//array(3) { [0]=> string(3) "one" [1]=> string(3) "two" [2]=> string(5) "three" }
$arrayChange = $arrayBase;
$arrayChange[0]='two';
var_dump($arrayChange);//array(3) { [0]=> string(3) "two" [1]=> string(3) "two" [2]=> string(5) "three" }
var_dump($arrayBase);//array(3) { [0]=> string(3) "one" [1]=> string(3) "two" [2]=> string(5) "three" }

//Object - is Reference Type:
class Example
{
private $v="first";
public function change()
{
$this->v="second";
}
public function echo()
{
echo $this->v;
}
}
$firstObject = new Example;
$secondObject = $firstObject;
$firstObject->echo();//first
$secondObject->change();
$firstObject->echo();//second
$secondObject->echo();//second
```

### SpetialTypes

Resource;
Null.

### PseudoTypes

Mixed;
Number;
callback (aka callable);
array|object;
Void.

### SuperglobalVariable

```php
$GLOBALS  //An array of variables that exist in th global scope
$_SERVER  //An array of info about paths, headers…
$_REQUEST //POST & GET request vars
$_POST    //Vars sent in POST request
$_GET     //Vars sent in GET request
$_ENV     //An associative array of vars passed via environment pethod
$_SESSION //An associative array of session vars
$_FILES   //An associative array of files that were uploaded as part of POST  request
```

### PredefinedConstants

```php
PHP_VERSION
PHP_EXTENSION_DIR
TRUE (boolean)
FALSE (boolean)
NULL
```

### ErrorMessageConstants

```php
E_ERROR
E_WARNING
E_PARSE
E_NOTICE
```

### MagicConstants

```php
__LINE__        //The current line number of the file.
__FILE__        //Full path and filename.
__DIR__         //File directory.
__FUNCTION__    //Function name
__CLASS__       //Class name

```

## References

By default, assignment operators work by value, that is, they copy the value of one expression to another. If the right operand is a variable, only its value is copied.</br>
But there are circumstances in which you might want the assignment to be by reference, so that the left operand becomes "bound" to the right.</br>

```php
//by value
$foo = 10;
$bar = $foo;
$bar = 20;
echo $foo; // Outputs 10

//by reference
$a = 10;
$b = &$a; // by reference
$b = 20;
echo $a; // Outputs 20

//the same for function:
//by value
function f($x) {
$x*=2;
}
$y=5;
f($y);
echo $y; // Outputs 5

//by reference
function f(&$x) {
$x*=2;
}
$y=5;
f($y);
echo $y; // Outputs 10
```

## RequireInclude

https://www.php.net/manual/ru/function.require.php</br>
https://www.php.net/manual/ru/function.include.php</br>
https://www.php.net/manual/ru/function.require-once.php</br>
https://www.php.net/manual/ru/function.include-once.php</br>

## Function

A function is a block of statements that can be reused in a program. </br>
In this block we can use any valid PHP code (include other Function and Class) </br>
Function in php have Global Scope (any function (made in any scope) can be call anywhere (unlike js where scope nested)) But online Compile don't do that!! so maybe this is not right.... or don't really right)</br>
Variable scope don't nested in inner function (unlike js) see example below. For visible need use like: (function () use ($arg))</br>

- [BuiltInFunction](#BuiltInFunction)
- [CustomFunctions](#CustomFunctions)
- [AnonimFunction](#AnonimFunction)
- [ArrowFunction](#ArrowFunction)
- [Scope&&Argument](#Scope&&Argument)
- [Closure](#Closure)
- [MemoizationCaching](#MemoizationCaching)

### BuiltInFunction

https://www.php.net/manual/ru/indexes.functions.php

### CustomFunctions

or user-defined functions </br>

https://www.php.net/manual/ru/functions.user-defined.php

```php
// defining as function (function declaration in js)
hello(); //Hello World!
function hello()
{
echo "Hello World!";
};
hello(); //Hello World!

//assigning an anonymous function to a variable (function expression in js)
$hello(); //ERROR
$hello=function()
{
echo "Hello World!";
};
$hello(); //Hello World!

//in php outer variables don't enter in scope inner function  (unlike js)
function outer(){
    $varOuter=55555;
    $inner=function() use ($varOuter){
     echo " outerscope $varOuter";
    };
      echo "inner $varOuter";//55555
      $inner();
};
outer();

```

### AnonimFunction

https://www.php.net/manual/ru/functions.anonymous.php

Anonim function can be static. In this case they don't bind with object</br>
```php
class Foo
{
    function __construct()
    {
        $func = static function() {  //Error (undefined this). Without "static"- object(Foo)#1 (0) 
            var_dump($this);
        };
        $func();
    }
};
new Foo();
```
Anonim function may also inherit variables from the parent scope. Any such variables must be passed to the "use" language construct. This case also call in PHP "closure"</br>

```php
$message = 'hello';
$example = function () use ($message) {
    var_dump($message);
};
$example(); //string(5) "hello"
```
### ArrowFunction

Arrow functions were introduced in PHP 7.4 as a more concise syntax for anonymous functions. </br>

```php
$y = 1; 
$fn1 = fn($x) => $x + $y; //in arrow function outer $y is defined
// equivalent to using $y by value:
$fn2 = function ($x) use ($y) { //in anonim function outer $y isn't defined (need Use)
    return $x + $y;
};
var_export($fn1(3)); //4

//case nested arrow function
$z = 1;
$fn = fn($x) => fn($y) => $x * $y + $z;
// Outputs 51
var_export($fn(5)(10));

```

### Scope&&Argument

```php
//dispatch several arguments ($numberTwo as default = 25, $variable is variable amount 0f values)
function sumFunction($numberOne, $numberTwo=25, ...$variable)
{
$sum = $numberOne + $numberTwo;
echo $sum, " ";
var_dump ($variable);
}
sumFunction(4,6); //10 array(0) { }
sumFunction(4); //29 array(0) { }
sumFunction(4,5,1,2,3,4); //9 array(4) { [0]=> int(1) [1]=> int(2) [2]=> int(3) [3]=> int(4) } 

//in php scope we can't nested value in inner function. 
//when we dispath type-value - type-value don't change (array in php also is type-value!).
$outer=5;
function innerF($argument)
{
echo $outer, " "; //_
$argument++;
echo $argument, " ";
}
innerF($outer); //6
echo $outer;//5

//we can't use outer variable by use "function () use ($arg)" in function-declaration
$message = '44444';
function example() use ($message) {
    var_dump($message);
};
example(); //Parse error: syntax error, unexpected 'use'

//we can use outer variable by use "function () use ($arg)" in function-expretion (anonim function)
$message = '44444';
$example = function () use ($message) {
    var_dump($message);
};
$example(); //44444

//we can dispatch parametr by reference:
function addFive(&$number)
{
$number += 5;
echo $number; //8
}
$test = 3;  
addFive($test);
echo $test;//8
```
### Closure

The same when Anonim function use inherit variables from the parent scope by "use". See example above.


### MemoizationCaching

Cache - is an intermediate buffer with fast access to it, containing information that can be requested with the highest probability. Accessing data in the cache is faster than fetching the original data from slower memory or a remote source, but its volume is significantly limited compared to the source data store. </br>

Memoization - is an optimization method that is mainly used to speed up computer programs by storing the results of expensive function calls and returning the cached result when calls on the same input data occur again . </br>

```php
function memoize($funcMem)
{
    return function () use ($funcMem) {
        static $cache = [];

        $args = func_get_args();
        //$key = serialize($args); //nativeExampleStupid))
        $key =$args[0];
        $cached = true;

        if (!isset($cache[$key])) {  //we can't use: $cache[$args[0]] without define: $key =$args[0]; May be BugPHP.
            $cache[$key] = $funcMem(...$args);
            $cached = false;
        }

        return ['result' => $cache[$key], 'cached' => $cached];
    };
}

$memoizedAdd = memoize(
    function ($num) {
        return $num + 10;
    }
);

var_dump($memoizedAdd(5));  
var_dump($memoizedAdd(6));  
var_dump($memoizedAdd(5));  
```

## Array

Array can store any type of data (numers, objects, etc.). ArrayIndex is Number and start from "0". </br>

```php
//there is several ways for create Arrays:
$firstArray = array("PHP", "JavaScript", "HTML"); 

$secondArray = array(  
0 => "PHP",
1 => "JavaScript",
2 => "HTML"
);

$thirdArray = array();
$thirdArray[0] = "PHP";
$thirdArray[1] = "JavaScript";
$thirdArray[2] = "HTML";

$months = array(  //associative Array
"march" => 31,
"april" => 30,
"may" => 31,
"june" => 30
);

//most usefull:
$test1=[1,2,3,4];

$test2=[];
$test2[0]=8;
$test2[1]=28;

$testAs=[           //associative Array
"march" => 31,
"april" => 30,
"may" => 31,
"june" => 30
];

//multidimensional arrays
$countries = array(  
"ukraine" => array("areas" => array("Kiev", "Poltava", "Lviv")
),
"usa" => array(
"areas" => array("Washington", "Texas")
)
);
echo "The capital of Ukraine is {$countries["ukraine"]["areas"][0]}"

//the same
$countries =[
    "ukraine" =>[
        "areas" => ["Kiev", "Poltava", "Lviv"],
        "rivers" => ["Dnipro", "Bug", "Dunay"],        
    ],
    "usa" =>[
        "areas" => ["Washington", "Texas"],
        "rivers" => ["Ukon", "Rio-Grande", "Ogayo"],        
    ]
    ];
echo "The capital of Ukraine is {$countries["ukraine"]["areas"][0]}"

```

## Class_Object

- [mainClassInfo](#mainClassInfo)
- [encapsulation](#encapsulation)
- [inheritance](#inheritance)
- [polymorphism](#polymorphism)
- [abstractClasses](#abstractClasses)
- [interfaces](#interfaces)


### mainClassInfo

Using a class, we declare a certain data structure. Оbject is an instance of a class. We can create an infinite number of objects of this class (create class instances).</br>

```php
class Example                       //class name start from uppercase letter
{
var $variable = "variableExample";  //member of class Variable (or creating Properties). Always Public as default. Modificator "public" will Wrong.
public function exampleMethod()            //member of class Method (method name start from lowercase letter)
{
return "methodExecuteResult";
}
public const CONSTANT = "constantExample"; //member of class CONSTANT (we can't use $ when define). We can get access to CONSTANT that way: Example::CONSTANT 
public static $variableStatic = "variableStaticExample"; //member of class StaticVariable. 
public static function staticFuncExample($param)
{
var_dump($param);
}
//We can get access to StaticVariable that way: Example::$variableStatic || Example::staticFuncExample("someValue");
//for access to Static member we need use "self" (this class) && "parent" (parent class):
//var_dump(self::$test, parent::$qwerty);

//property, getter, setter
private $props; // member of class Property
public function getProps() //member of class Getter
{
return $this->props; //$this - contex of object from that class
}
public function setProps($props) //member of class Setter
{
$this->props = ucwords(strtolower($props)); //$this - contex of object from that class
}

}

$obj = new Example();               //object name start from lowercase letter    
var_dump($obj);
var_dump($obj->variable); //variableExample
var_dump(Example::$variableStatic); //variableStaticExample
Example::staticFuncExample("someValue"); //someValue
var_dump(Example::CONSTANT); //constantExample
var_dump($obj->exampleMethod()); //methodExecuteResult

$obj->setProps("propertyValue");
var_dump($obj->getProps()); //propertyValue
```

### encapsulation
Encapsulation - the union of several elements in one isolated entity (for example, in a class), when the elements of this entity are isolated from other code elements. </br>
We have 3 access modificators:</br>
- "public" - this member can be accessed by any other code in the application.</br>
- "protected" - the member can only be accessed by code in the same class or in a class derived from this class.</br>
- "private" - the member can only be accessed by code from the same class.</br>
By default, all class members are public, but it's good practice to declare this explicitly.</br>

### inheritance
Inheritance - creation of child classes based on the base class (Best practice is use  Composition or Aggregation with Abstract Class or Interface(see Patterns below)).</br>

```php
class Base
{
  var $variable = "variableBase"; //we can't use 3 access modificators for "var" - this is Public as default
  public  const CONSTANT = "constantBase"; 
}

class NextBase extends Base
{
   var $nextVariable = "variableNextBase"; //we can't use 3 access modificators for "var" - this is Public as default
   public const NEXTCONSTANT = "constantNextBase"; 
} 

$exampleInheritance= new NextBase(); 
var_dump($exampleInheritance->variable);
var_dump($exampleInheritance->nextVariable);
var_dump(NextBase::CONSTANT);
var_dump(NextBase::NEXTCONSTANT);

```

### polymorphism
Polymorphism. Basic definition: one interface and many implementations (this also includes function overloads and so on, which allows the same functionality to process data of different types - the general classical definition of polymorphism).</br>
In PHP polymorphism as rule use in AbstractClasses and Interfaces.</br>

### abstractClasses
Abstract Classes:</br>

```php
abstract class Builder {//we can't create new abstract class "new Builder" - only implementations
    abstract public function build();
    //in abstract class we also can use All other ClassMembers (var, const, props, not abstract methods etc), as example:
    public  const CONSTANT = "constantAbstractExample";
}

class WoodBuilder extends Builder {//first implementation of abstractClass Builder
    public function build(){
        echo "Build wood house \n";
    }    
} 

class ConcreteBuilder extends Builder {//second implementation of abstractClass Builder
      public function build(){
        echo "Build concrete house \n";
    }      
} 

$wb = new WoodBuilder;
$cb = new ConcreteBuilder;

//now we can get access to different functions in different objects (from different classes) by common interface (abstract class Builder):

function tryBuild (Builder $b){
    $b->build();
}

tryBuild($wb); //Build wood house
tryBuild($cb); //Build concrete house
var_dump(WoodBuilder::CONSTANT); //constantAbstractExample
var_dump(ConcreteBuilder::CONSTANT); //constantAbstractExample
echo Builder::CONSTANT; //constantAbstractExample

```

### interfaces
Interfaces:</br>

```php
//in an interface, unlike abstract classes, we can only define abstract methods and CONSTANTS (as default all methods is abstract, the word Abstract is not used). All other ClassMember we can't create in interface.
interface IBuilder{//we can't create new class "new IBuilder" - only implementations
    public function build(); 
     public  const CONSTANT = "constantInterfaceExample";
}

class WoodBuilder implements IBuilder {//first implementation of interface IBuilder
    public function build(){
        echo "Build wood house \n";
    }    
} 

class ConcreteBuilder implements IBuilder {//second implementation of interface IBuilder
      public function build(){
        echo "Build concrete house \n";
    }      
} 

$wb = new WoodBuilder;
$cb = new ConcreteBuilder;

//now we can get access to different functions in different objects (from different classes) by common interface (interface IBuilder):

function tryBuild (IBuilder $b){
    $b->build();
}

tryBuild($wb); //Build wood house
tryBuild($cb); //Build concrete house
var_dump(WoodBuilder::CONSTANT); //constantInterfaceExample
var_dump(ConcreteBuilder::CONSTANT); //constantInterfaceExample
echo IBuilder::CONSTANT; //constantInterfaceExample

//interfaces can inherit other (several other) interface by "extends":
interface A
{
    public function foo();
}
interface B extends A
{
    public function baz(Baz $baz);
}
interface C extends A, B
{
    public function baz();
}

//one class can impliments several interfaces:
class MyClass implements A, B{}

//word "extends" need put until "impliments":
class Two extends One implements Usable, Updatable {} 
```

## SQL

- [mainSqlInfo](#mainSqlInfo)
- [relationships](#relationships)
- [normalization](#normalization)
- [primaryKey](#primaryKey)
- [foreignKey](#foreignKey)
- [dataType](#dataType)
- [constraints](#constraints)
- [mainComands](#mainComands)


### mainSqlInfo
SQL - Structured Query Language. </br>
This is declarative programming language for interacting with relational databases.</br>
DBMS - database management systems (is the software that interacts with end users, applications, and the database itself to capture and analyze the data). There are several DBMS based on SQL (each with own procedural variety of SQL): </br>

MySQL 	                            - SQL/PSM 	(SQL/Persistent Stored Module) </br>
Oracle 	                            - PL/SQL 	(Procedural Language/SQL)</br>
Microsoft SQL Server/Sybase ASE 	- Transact-SQL </br>
PostgreSQL 	                        - PL/pgSQL 	(Procedural Language/PostgreSQL)</br>
Borland InterBase/Firebird 	        - PSQL (Procedural SQL) </br> 
IBM DB2 	                        - SQL PL 	(SQL Procedural Language) </br>

### relationships
Between the elements of relativistic databases there are the following possible relationships:</br>
1. One to one (One Country to One Capital).</br>
2. One to many (One Country to Many Сities). </br>
3. Many to many (Many Rivers to Many Countries (through which they go)). For this case need third additional table (where we will make reference between id from 2 main tables).</br>

### normalization
The process of dividing elements of relativistic databases into elementary tables is called database normalization.</br>
1. First normal form (1NF). Two rows of the table should not be repeated (have the same content). Each row must have a unique primary key (usually an ID). No table cell should contain multiple values (for example, separated by commas).The order of columns and rows does not matter (makes no sense). Columns have no sub-columns (splits)</br>
2. Second normal form (2NF). (2NF use for composite primary keys. As rule in BD we use ID - not  composite primary key. In case using ID, 2NF we don't need). So 2NF say: for composite primary keys all data in each table cell must depend on all parts of composite primary keys. As example: primary key <StudentName && Adress> and Column <Faculty> - 2NF not complied with (<Faculty> don't depend on <Adress>).</br>
3. Third normal form (3NF). There should not be a transitive dependence of non-key elements in the string (that is, one non-key element should not depend on another so that there is no duplication of data). As example: primary key <exam && dataTime>, first non-key column <student>, second non-key column <dataBithday>. 3NF not complied with (<dataBithday> depend on <student>. So if the same student is registered for another exam, we will have to unnecessarily duplicate his date of birth as well).</br>

### primaryKey
Primary Key - every table must have One Primary Key (consisted from one or several column). This Primary Key is unike (as default) for each row. As rule Primary Key is comlumn ID (generated automaticaly)</br>

### foreignKey
Foreign keys are used to create relationships between tables. In fact, these are links to a column of another table (usually to the columns of the primary key ID) ( FOREIGN KEY (StudentId)  REFERENCES Students (Id))</br>

With a possible deletion or change of a foreign key (to preserve the integrity of the database), the following commands are used:</br>
1. ON DELETE - sets the actions to be taken when a related row is removed from the main table</br>
2. ON UPDATE - sets the actions to be taken when a related row is changed in the main table</br>

#### Attributes this commands:
1. CASCADE - automatically deletes or changes rows from a dependent table when related rows in the master table are deleted or changed (ON DELETE CASCADE, ON UPDATE CASCADE)</br>
2. SET NULL - when deleting or updating a related row from the main table, sets the foreign key column to NULL. (In this case, the foreign key column must support NULL value). (ON DELETE SET NULL, ON UPDATE SET NULL)</br>
3. RESTRICT - rejects deleting or modifying rows in the parent table if there are related rows in the dependent table. (ON DELETE RESTRICT, ON UPDATE RESTRICT)</br>
4. NO ACTION: - rejects deleting or modifying rows in the parent table if there are related rows in the dependent table. (ON DELETE NO ACTION, ON UPDATE NO ACTION)</br>
5. SET DEFAULT: - when deleting a related row from the main table, sets the foreign key column to the default value, which is set using the DEFAULT attributes. Not recommended because not all databases support this functionality</br>

### dataType
SQL Data Type</br>
https://www.w3schools.com/sql/sql_datatypes.asp</br>

### constraints
https://www.w3schools.com/sql/sql_constraints.asp</br>
SQL constraints are used to specify rules for the data in a table (NOT NULL, UNIQUE, PRIMARY KEY, FOREIGN KEY, CHECK, DEFAULT, CREATE INDEX).</br>

### mainComands

https://www.w3schools.com/sql/default.asp </br>

SHOW DATABASES;</br>
CREATE DATABASE exampleDB;</br>
USE exampleDB;</br>
DROP DATABASE exampleDB;</br>
DROP DATABASE exampleDB;</br>
BACKUP DATABASE exampleDB
TO DISK = 'filepath'; </br>
DROP DATABASE exampleDB;</br>
CREATE TABLE Students (
    StudentID int,
    LastName varchar(255),
    FirstName varchar(255)    
);</br>
DROP TABLE Students; </br>
INSERT INTO Students (first_name, last_name) VALUES ('Bill', 'Tuclgunnery');</br>
SELECT * FROM Students;</br>
SELECT FirstName, LastName FROM Students;</br>
SELECT * FROM Students WHERE id > 22 AND FirstName = 'Bill';</br>
SELECT * FROM Students WHERE id > 22 OR FirstName = 'Bill';</br>
SELECT * FROM Students WHERE FirstName LIKE 'B%'; //select all names wich starting from B ("%"-several simbols, "_" - one simbol)</br>

SELECT * FROM Students ORDER BY id ASC; (sort by ascending  (DESC - descending))</br>

#### AgregatFunction: 
COUNT() //count the number of rows that match certain conditions</br>
 MAX()  //returns max value of column </br>
 MIN()  //returns min value of column </br>
 SUM()  //function returns the total sum of a column </br>
 AVG()  //returns the average value of a column </br>

SELECT COUNT(CustomerID), Country FROM Customers GROUP BY Country ORDER BY COUNT(CustomerID) DESC; //"GROUP BY" we use with AgregateFunction: COUNT(), MAX(), MIN(), SUM(), AVG() </br>

SELECT DISTINCT Scholarship FROM Students; //DISTINCT are eliminated duplicate values</br>
DELETE FROM Students WHERE id > 24;</br>
DROP TABLE Students;</br>

#### JOIN
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.</br>
We can use: (INNER) JOIN, LEFT (OUTER) JOIN, RIGHT (OUTER) JOIN, FULL (OUTER) JOIN </br>

As example we have 2 tables: </br>
1. Orders (OrderID 	CustomerID 	OrderDate)</br>
2. Customers (CustomerID 	CustomerName 	ContactName 	Country)</br>

#### (INNER) JOIN: 
Returns table (consisted of column diferent tables DB) that have matching values in both tables.</br>

SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate</br>
FROM Orders</br>
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;</br>

We get result table with column: OrderID (from Orders), CustomerName (from Customers), OrderDate (from Orders). And rows, that will have only those values, wich meet the condition (Orders.CustomerID=Customers.CustomerID) on both tables (Orders && Customers). That is, we will get rows with all customer orders with customer names and order dates. Customers who did not place orders are not displayed. And orders without customer names too are not displayed (if possible))))!</br>

#### LEFT (OUTER) JOIN:
 Returns table (consisted of column diferent tables DB) wich will have all records from the left table, and the matched records from the right table.</br>

SELECT Customers.CustomerName, Orders.OrderID</br>
FROM Customers</br>
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID</br>
ORDER BY Customers.CustomerName;</br>

We get result table with column: CustomerName (from Customers), OrderID (from Orders). And rows, that will have:</br>
- all records from the left table (CustomerName (from Customers)).
- only those values, wich meet the condition (Customers.CustomerID = Orders.CustomerID) from the right table (OrderID (from Orders)). </br>
That is, we will get rows with all customers (even witout orders) and orders (wich meet the condition...). Orders without customer names are not displayed (if possible))))!</br>


#### RIGHT (OUTER) JOIN: 
Returns table (consisted of column diferent tables DB) wich will have the matched records from the left table and all records from the right table.</br>

SELECT Customers.CustomerName, Orders.OrderID</br>
FROM Customers</br>
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID</br>
ORDER BY Customers.CustomerName;</br>

We get result table with column: CustomerName (from Customers), OrderID (from Orders). And rows, that will have:</br>
- only those values, wich meet the condition (Customers.CustomerID = Orders.CustomerID) from the left table (CustomerName (from Customers)). </br>
- all records from the right table (OrderID (from Orders)).
That is, we will get rows with customers (wich meet the condition...) and orders (even witout customers .... if it possible))). Customers without orders are not displayed.</br>


#### FULL (OUTER) JOIN: 
Returns table (consisted of column diferent tables DB) wich will have all records from the left table and all records from the right table.</br>

SELECT Customers.CustomerName, Orders.OrderID</br>
FROM Customers</br>
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID</br>
ORDER BY Customers.CustomerName;</br>

We get result table with column: CustomerName (from Customers), OrderID (from Orders). And rows, that will have:</br>
- all records from the left table (CustomerName (from Customers)). </br>
- all records from the right table (OrderID (from Orders)).
That is, we will get rows with customers (even witout orders) and orders (even witout customers .... if it possible))). So condition (Customers.CustomerID = Orders.CustomerID) in this case will ignored for both tables.</br>

## DRY_YAGNI_KISS_SOLID

#### DRY
 which stands for ‘don’t repeat yourself,’ is a principle of software development that aims at reducing the repetition of patterns and code duplication in favor of abstractions and avoiding redundancy. So if you see what your code need repeated parts, then repeated parts of code need put into a separate functional (function, class ...).</br>

#### YAGNI
 principle ("You Aren't Gonna Need It") is a practice in software development which states that features should only be added when required. As a part of the extreme programming (XP) philosophy, YAGNI trims away excess and inefficiency in development to facilitate the desired increased frequency of releases.</br>

#### KISS
 principle ("Keep it simple stupid (Keep It Short and Simple)") is a practice in software development which states that technical solutions should be as simple as possible (but no more simple than possible)))! Echoes YAGNI.</br>

#### SOLID
S_ingle Responsibility Principle </br>
O_pen/Closed Principle </br>
L_iskov Substitution Principle </br>
I_nterface Segregation Principle </br>
D_ependency Inversion Principle</br>

In general, we can say that the SOLID principle is needed to create a flexible and editable code (divided into certain parts), in which, if necessary, change (delete, add) some part of the code, you do not need to go through, change and recheck ALL code, just change (add , remove) some small (encapsulated) parts without changing and checking the rest of the code.</br>

That is, to understand all these principles, it is necessary to understand that in the end we strive to freely change (add, replace, delete) some part of the code, leaving the rest of the code unchanged. The same applies to patterns (mvс, etc. - see below)</br>

#### Single Responsibility Principle 
Each component of the code (class, method, etc.) should have a single responsibility, that is, perform a single task. For example, in a programLibrary, we need a class to print a book (this is the only responsibility). If we add the book search functionality to those class, this is a violation of this principle.</br>

#### Open/Closed Principle
Program components must be open for extension but closed for modification. The program should be built in such a way that all its subsequent changes should be implemented by adding new code, and not changing the existing one (at least this should be strived for))). Of course, this applies to the functionality planned for change.</br>
For example, we have a Programmer class that can write C programs. But initially we assume that his skills will expand and improve over time. Accordingly, in order to add a PHP programming skill, we should use this principle - we should not change anything - just add a new component to the existing ones (for example, an associative array of Skills with elements with a common interface, etc.)</br>

#### Liskov Substitution Principle 
This principle requires: in the case of using its derived (child) elements instead of the base (parent) element, the general functionality of the program should not change. That is, we should be able to use derived elements from the base ones without violating the logic of the program.

#### Interface Segregation Principle
Interfaces should contain only the functionality that is used in the elements (classes) that depend on them. That is, if an interface contains a method definition, and this method is not implemented and not used in a class that depends on it, this is a violation of this principle. It looks like the single responsibility principle - for its implementation it is necessary to split the interfaces into elementary components, not to use bold and bloated interfaces.</br>

#### Dependency Inversion Principle
Program elements that use the functionality of other program elements should not depend on their functionality (for example, on their methods) directly. This dependency should be implemented through abstractions (abstract classes, interfaces).</br>
For example, we have previous-level class (on which we depend) with some methods. This methods we need use in a next-level class (dependent), using association (composition, aggregation) (see below). According to this principle, in this case we need to additionally create an abstraction (abstract class, interface). This abstraction will be implemented by our previous-level class (on which we depend). And we will transfer the abstraction to the next-level class (dependent), in which we will use the methods of the previous-level class (on which we depend) using the abstraction in which they were defined.</br>

## UML
https://en.wikipedia.org/wiki/Class_diagram
https://metanit.com/sharp/patterns/1.2.php

#### UML - Unified Modeling Language. 
UML is an open standard that uses graphical notation to create an abstract model of a system, called a UML model. The UML was created to define, visualize, design and document, basically, software systems. UML is not a programming language, but code generation is possible based on UML models.</br>

#### In softDevelopment as rule we use only UML part - class diagram.

The class is the key element in object-oriented modeling. In the diagram, the classes are presented in boxes containing three components:
1. At the top - the class name (in bold and centered, and the first letter is capitalized).</br>
2. At center - fields of the class (left-aligned and the first letter is lowercase).</br>
3. At bottom - the class methods (left-aligned and the first letter is lowercase).</br>

#### Visibility.
Visibility of a class member must be placed before their name.</br>
+/ 	Public</br>
-/ 	Private</br>
#/ 	Protected</br>
~/ 	Package </br>
Also we use "/" before derived properties (props use outer sourses (other props etc))</br>

#### Scopes.
The UML specifies two types of scope for members:</br>
- Instance members (not underlined names). Are scoped to a specific instance. Attribute values may vary between instances. Method invocation may affect the instance’s state (i.e. change instance’s attributes).</br>
- Class members or Static members (underlined names). The scope end is the class itself. Attribute values are equal for all instances. Method invocation does not affect the classifier’s state.</br>

#### Relationships.
!!!! General rule - the arrow is always directed from the next-level class (dependent or derived or children or subclass or assebly etc) to the previous-level class (on which we depend or parent or superclass or component etc). That is there is inversion (from complex to simple or from end to beginning) (as usually - really CLEVER!!)). Please note that for aggregation and composition, a rhombus is not an arrow (there are both arrows and rhombuses)</br>
<p align="center">
  <img src="/img/relationships.png" width="450" title="hover text"> 
</p>

#### 1. Instance-level relationships.

#### 1.1 Dependency. 
<p align="center">
  <img src="/img/depend.png" width="450" title="hover text"> 
</p>
 Exists between two elements if changes to the definition of one element (previous-level class (on which we depend) - the server or target)))) may cause changes to the other (next-level class (dependent)- the client or source)))).</br>
 As example we use method of previous-level class (on which we depend) in next-level class (dependent). In this case if we will change those method in previous-level class (on which we depend) - this changes will influence on next-level class (dependent) making him dependent.</br>
 Please note that in accordance with the SOLID principle, the dependency must be made using additional abstractions (see above).</br>

#### 1.2 Association.
<p align="center">
  <img src="/img/assoc.png" width="450" title="hover text"> 
</p>

```php
class Team{ 
}
class Player{   
 public Team Team { get; set; }
}
```
An association is a relationship in which objects of one type are related in some way to objects of another type.</br>
An association can link any number of classes. </br>
There are four different types of association: bi-directional, uni-directional, aggregation (includes composition aggregation) and reflexive.</br>
Aggregation and composition are special cases of association.</br>

#### 1.3 Aggregation.
<p align="center">
  <img src="/img/agreg.png" width="450" title="hover text"> 
</p>

```php
public abstract class Engine
{ }
 
public class Car
{
    Engine engine;
    public Car(Engine eng)
    {
        engine = eng;
    }
}
```
Aggregation is a special case of association.</br>
An aggregation may not involve more than two classes; it must be a binary association. </br>
It assumes a HAS A relationship between classes (that is, one class has another class). Implemented accordingly using the constructor (as a rule) but previous-level class (component or content) is not created in it, but imported from outside.</br>

Aggregation relationship</br>
    1. When representing a software or database relationship, e.g. car model engine ENG01 is part of a car model CM01, as the engine, ENG01, maybe also part of a different car model.</br>
    2. When the container is destroyed, the contents are usually not destroyed, e.g. a professor has students; when the professor leaves the university the students do not leave along with them.</br>

#### 1.4 Composition.
<p align="center">
  <img src="/img/compos.png" width="450" title="hover text"> 
</p>

```php
public class ElectricEngine
{ }
 public class Car{
   ElectricEngine engine;
    public Car()
    {
        engine = new ElectricEngine();
    }
}
```
Composition is a special case of association.</br>
An composition may not involve more than two classes; it must be a binary association. </br>
It assumes a HAS A relationship between classes (that is, one class has another class). Implemented accordingly using the constructor (as a rule), object of previous-level class (component or content) is created in in those constructonr by use "new".</br>

Composition relationship</br>
    1. When attempting to represent real-world whole-part relationships, e.g. an engine is a part of a car.</br>
    2. When the container is destroyed, the contents are also destroyed, e.g. a university and its departments.</br>

#### 2.Class-level relationships

#### 2.1 Inheritance (Generalization)
Allows one class (child or subclass) to inherit the functionality of another class (parent or superclass).</br>

```php
class User
{
    public int Id { get; set; }
    public string Name { get; set; }
}
 
class Manager : User
{
    public string Company{ get; set; }
}
```
<p align="center">
  <img src="/img/inh.png" width="190" title="hover text"> 
</p>

#### 2.2 Realization (Implementation)
Realization - is a relationship between two model elements, in which one model element (the client) realizes (implements or executes) the behavior that the other model element (the supplier) specifies. As example: Interface-Class/
```php
public interface IMovable
{
    void Move();
}
public class Car : IMovable
{
    public void Move()
    {
        Console.WriteLine("Машина едет");
    }
}
```
<p align="center">
  <img src="/img/realiz.png" width="190" title="hover text"> 
</p>


## Patterns

https://refactoring.guru/design-patterns

Design patterns are typical solutions to common problems
in software design.</br>

#### Creational Design Patterns. </br>
Creational design patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.</br>

1. Factory Method </br>
Factory Method is a creational design pattern that provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created.</br>
https://refactoring.guru/design-patterns/factory-method  (see Structure UML)</br>
https://refactoring.guru/design-patterns/factory-method/php/example

2. Abstract Factory </br>
Abstract Factory is a creational design pattern that lets you produce families of related objects without specifying their concrete classes.</br>
https://refactoring.guru/design-patterns/abstract-factory (see Structure  UML)</br>
https://refactoring.guru/design-patterns/abstract-factory/php/example

3. Builder </br>
Builder is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.</br>
https://refactoring.guru/design-patterns/builder (see Structure  UML)</br>
https://refactoring.guru/design-patterns/builder/php/example

4. Singleton </br>
Singleton is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.</br>
https://refactoring.guru/design-patterns/singleton  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/singleton/php/example

5. Prototype </br>
Prototype is a creational design pattern that lets you copy existing objects without making your code dependent on their classes.</br>
https://refactoring.guru/design-patterns/prototype  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/prototype/php/example

#### Structural Design Patterns. </br>
Structural design patterns explain how to assemble objects and classes into larger structures, while keeping these structures flexible and efficient.</br>

1. Adapter </br>
Adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.</br>
https://refactoring.guru/design-patterns/adapter   (see Structure  UML)</br>
https://refactoring.guru/design-patterns/adapter/php/example

2. Bridge </br> 
Bridge is a structural design pattern that lets you split a large class or a set of closely related classes into two separate hierarchies—abstraction and implementation—which can be developed independently of each other.</br>
https://refactoring.guru/design-patterns/bridge  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/bridge/php/example

3. Composite </br> 
Composite is a structural design pattern that lets you compose objects into tree structures and then work with these structures as if they were individual objects.</br> 
https://refactoring.guru/design-patterns/composite  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/composite/php/example

4. Decorator </br> 
Decorator is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.</br> 
https://refactoring.guru/design-patterns/decorator  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/decorator/php/example

5. Facade </br> 
Facade is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes.</br> 
https://refactoring.guru/design-patterns/facade  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/facade/php/example

6. Flyweight </br> 
Flyweight is a structural design pattern that lets you fit more objects into the available amount of RAM by sharing common parts of state between multiple objects instead of keeping all of the data in each object.</br> 
https://refactoring.guru/design-patterns/flyweight  (see Structure  UML)</br>
https://refactoring.guru/design-patterns/flyweight/php/example

7. Proxy </br> 
Proxy is a structural design pattern that lets you provide a substitute or placeholder for another object. A proxy controls access to the original object, allowing you to perform something either before or after the request gets through to the original object.</br> 
https://refactoring.guru/design-patterns/proxy (see Structure  UML)</br>
https://refactoring.guru/design-patterns/proxy/php/example

#### Behavioral Design Patterns </br>
Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects. </br>

1. Chain of Responsibility </br> 
Chain of Responsibility is a behavioral design pattern that lets you pass requests along a chain of handlers. Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain.</br> 
https://refactoring.guru/design-patterns/chain-of-responsibility (see Structure  UML)</br>
https://refactoring.guru/design-patterns/chain-of-responsibility/php/example

2. Command (action, transaction) </br> 
Command is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you pass requests as a method arguments, delay or queue a request’s execution, and support undoable operations.</br> 
https://refactoring.guru/design-patterns/command (see Structure  UML)</br>
https://refactoring.guru/design-patterns/command/php/example

3. Iterator </br> 
Iterator is a behavioral design pattern that lets you traverse elements of a collection without exposing its underlying representation (list, stack, tree, etc.).</br> 
https://refactoring.guru/design-patterns/iterator (see Structure  UML)</br>
https://refactoring.guru/design-patterns/iterator/php/example

4. Mediator </br> 
Mediator is a behavioral design pattern that lets you reduce chaotic dependencies between objects. The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.</br> 
https://refactoring.guru/design-patterns/mediator (see Structure  UML)</br>
https://refactoring.guru/design-patterns/mediator/php/example

5. Memento </br> 
Memento is a behavioral design pattern that lets you save and restore the previous state of an object without revealing the details of its implementation.</br> 
https://refactoring.guru/design-patterns/memento (see Structure  UML)</br>
https://refactoring.guru/design-patterns/memento/php/example

6. Observer </br> 
Observer is a behavioral design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing.</br> 
https://refactoring.guru/design-patterns/observer (see Structure  UML)</br>
https://refactoring.guru/design-patterns/observer/php/example

7. State </br> 
State is a behavioral design pattern that lets an object alter its behavior when its internal state changes. It appears as if the object changed its class.</br> 
https://refactoring.guru/design-patterns/state (see Structure  UML)</br>
https://refactoring.guru/design-patterns/state/php/example

8. Strategy </br> 
Strategy is a behavioral design pattern that lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.</br> 
https://refactoring.guru/design-patterns/strategy (see Structure  UML)</br>
https://refactoring.guru/design-patterns/strategy/php/example

9. Template Method </br> 
Template Method is a behavioral design pattern that defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.</br> 
https://refactoring.guru/design-patterns/template-method (see Structure  UML)</br>
https://refactoring.guru/design-patterns/template-method/php/example

10. Visitor </br> 
Visitor is a behavioral design pattern that lets you separate algorithms from the objects on which they operate.</br> 
https://refactoring.guru/design-patterns/visitor (see Structure  UML)</br>
https://refactoring.guru/design-patterns/visitor/php/example


## MVC

https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller</br>
https://ru.wikipedia.org/wiki/Model-View-Controller</br>


Model-View-Controller (MVC) - a scheme for dividing application data and control logic into three separate components: model, view and controller - so that each component can be modified independently</br>

Since MVC does not have a strict implementation, it can be implemented in different ways. In general, we can display:</br>

<p align="center">
  <img src="/img/mvc.png" width="450" title="hover text"> 
</p>

The main and basic principle of the implementation of the MVС is that the Model, View and Controller should be independent of each other in terms of development and replacement (that is, the Model developer, for example, does not need to know what the View and Controller do; the Model (as well as other components) should be possible to be replaced without changing the Controller and View). Also, as a rule, they try to place business logic (im MVC business logic - this is as rule involves processing data in a database) in the Model (avoiding Bold and Thick Controllers). The controller must be thin!!</br>

- Model provides data and responds to controller commands by changing its state. </br>
- View is responsible for displaying model data to the user, reacting to model changes. </br>
- Controller interprets the user's actions, notifying the model of the need for changes. </br>

## LARAVEL

https://laravel.com/

//laravel API
https://laravel.com/api/9.x/

## Middleware

https://laravel.com/api/9.x/Illuminate/Auth/Middleware.html

## ContractsHelpers

https://laravel.com/api/9.x/Illuminate/Contracts.html </br>

Contract - this is Interface. </br>
Recommend to place custom Contracts in folder App/Contracts.

```php
 interface SaveImage{
      public static function save();
      public static function delete();
}
```

Helpers - this is implement of interfaces. </br>
Recommend to place custom Helpers in folder App/Helpers.

```php
 class SaveImageDisk implements SaveImage{
    public static function save (){
           //process saving on disk
    }
    public static function delete(){
           //process deleting from disk
    }
}

 class SaveImageAws implements SaveImage{
      public static function save (){
           //process saving on aws
      }
      public static function delete(){
           //process deleting from aws
      }
}
```

## ServiceContainer

https://laravel.com/docs/9.x/container

api:
https://laravel.com/api/9.x/Illuminate/Contracts/Container/Container.html

The Laravel service container is a powerful tool for managing class dependencies and performing dependency injection. Dependency injection is a fancy phrase that essentially means this: class dependencies are "injected" into the class via the constructor or, in some cases, "setter" methods. </br>

Thanks to zero configuration resolution, you will often type-hint dependencies on routes, controllers, event listeners, and elsewhere without ever manually interacting with the container. For example, you might type-hint the Illuminate\Http\Request object on your route definition so that you can easily access the current request. Even though we never have to interact with the container to write this code, it is managing the injection of these dependencies behind the scenes: </br>

```php
//In many cases, thanks to automatic dependency injection and facades, you can build Laravel applications without ever manually binding or resolving anything from the container.
use Illuminate\Http\Request;
Route::get('/', function (Request $request) {
    // ...
});
```

Manually interact with the container need when: </br>

1.  If you write a class that implements an interface and you wish to type-hint that interface on a route or class constructor, you must tell the container how to resolve that interface. (in our example (see below) we will use throgh ServiceProvider method Bind (within any ServiceProvider methods, we always have access to the $app property which provides access to the service container)) --- $this->app->bind('App\Contracts\SaveImage', function(){....</br>
2.  If you are writing a Laravel package that you plan to share with other Laravel developers, you may need to bind your package's services into the container.</br>

## ServiceProviders

https://laravel.com/docs/9.x/providers</br>

not realy right but particulary)):</br>
https://vue-laravel.blogspot.com/2018/07/laravel.html</br>

$ php artisan make:provider ExampleServiceProvider $</br>

One of the most important kernel bootstrapping actions is loading the service providers for your application. Service providers are responsible for bootstrapping all of the framework's various components, such as the database, queue, validation, and routing components. All of the service providers for the application are configured in the config/app.php configuration file's providers array. Many of these providers are "deferred" providers, meaning they will not be loaded on every request, but only when the services they provide are actually needed.</br>

All service providers extend the Illuminate\Support\ServiceProvider class. Most service providers contain a register and a boot method. </br>

Within any of your service provider methods, you always have access to the $app property which provides access to the service container:</br>
https://laravel.com/api/9.x/Illuminate/Contracts/Container/Container.html</br>

1. The Register Method.</br>
   Within the register method, you should only bind things into the service container. You should never attempt to register any event listeners, routes, or any other piece of functionality within the register method. Otherwise, you may accidentally use a service that is provided by a service provider which has not loaded yet.</br>

```php
//for example above
 public function register (){
     $this->app->bind('App\Contracts\SaveImage', function(){
            return new saveImageAws();
            //return new saveImageDisk();
     });
}
//also:
//https://laravel.com/docs/9.x/providers#the-register-method
//binding, singlton
//https://laravel.com/docs/9.x/providers#the-bindings-and-singletons-properties
```

2. The Boot Method.</br>
   For register a view composer within our service provider - this should be done within the boot method. This method is called after all other service providers have been registered, meaning you have access to all other services that have been registered by the framework:

```php
namespace App\Providers;

use Illuminate\Support\Facades\View;
use Illuminate\Support\ServiceProvider;
class ComposerServiceProvider extends ServiceProvider
{

    public function boot()
    {
        View::composer('view', function () {
            //
        });
    }
}
//You may type-hint dependencies for your service provider's boot method. The service container will automatically inject any dependencies you need:
use Illuminate\Contracts\Routing\ResponseFactory;
public function boot(ResponseFactory $response)
{
    $response->macro('serialized', function ($value) {
        //
    });
}
//for use in Blade directive (see Roles && Permissions):
use Illuminate\Support\Facades\Blade;
use Illuminate\Support\ServiceProvider;
 public function boot()
    {
        Blade::directive('role', function ($role) {
            return "<?php if(auth()->check() && auth()->user()->hasRole({$role})): ?>";
        });
        Blade::directive('endrole', function ($role) {
            return "<?php endif; ?>";
        });
    }
```
