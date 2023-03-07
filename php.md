# PHP Manual

<p align="center">
  <img src="/img/55.png" width="350" title="hover text"> 
</p>

## Content

- [Generalinfo](#Genera_info)
- [PHPTags](#PHPTags)
- [DataTypeVariables](#DataTypeVariables)
- [References](#References)
- [RequireInclude](#RequireInclude)
- [Function](#Function)
- [Array](#Array)
- [Class_Object](#Class_Object)
- [SQL](#SQL)

- [LARAVEL](#LARAVEL)
- [Middleware](#Middleware)
- [ContractsHelpers](#ContractsHelpers)
- [ServiceContainer](#ServiceContainer)
- [ServiceProviders](#ServiceProviders)

## Genera_info

PHP - Hypertext Preprocessor </br>
https://www.php.net/</br>

online compile PHP</br>
https://www.w3schools.com/php/phptryit.asp?filename=tryphp_compiler</br>
https://onecompiler.com/php/3yq869cmt</br>

## PHPTags

https://www.php.net/manual/ru/language.basic-syntax.phptags.php

```php
<?php echo 'Print' ?>
//echo tag
<?= 'Print' ?>

//If a file contains only PHP code (without HTML), it is preferable to omit the PHP closing tag at the end of the file (becouse php can to start output buffering Spase or NewLine (Enter) when there is no intention).
<?php echo 'Print'

//!!!!!short sintax can be enabled or disabled by option short_open_tag in php.ini, so NOT USE IT!!!
<? echo 'Print' ?>

```

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

https://www.php.net/manual/ru/function.require.php
https://www.php.net/manual/ru/function.include.php
https://www.php.net/manual/ru/function.require-once.php
https://www.php.net/manual/ru/function.include-once.php

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

SQL - Structured Query Language. </br>
This is declarative programming language for interacting with relational databases.</br>
DBMS - database management systems (is the software that interacts with end users, applications, and the database itself to capture and analyze the data). There are several DBMS based on SQL (each with own procedural variety of SQL): </br>

MySQL 	                            - SQL/PSM 	(SQL/Persistent Stored Module) </br>
Oracle 	                            - PL/SQL 	(Procedural Language/SQL)</br>
Microsoft SQL Server/Sybase ASE 	- Transact-SQL </br>
PostgreSQL 	                        - PL/pgSQL 	(Procedural Language/PostgreSQL)</br>
Borland InterBase/Firebird 	        - PSQL (Procedural SQL) </br> 
IBM DB2 	                        - SQL PL 	(SQL Procedural Language) </br>


Between the elements of relativistic databases there are the following possible relationships:</br>
1. One to one (One Country to One Capital).</br>
2. One to many (One Country to Many Сities). </br>
3. Many to many (Many Rivers to Many Countries (through which they go)). For this case need third additional table (where we will make reference between id from 2 main tables).</br>

The process of dividing elements of relativistic databases into elementary tables is called database normalization.</br>
1. First normal form (1NF). Two rows of the table should not be repeated (have the same content). Each row must have a unique primary key (usually an ID). No table cell should contain multiple values (for example, separated by commas).The order of columns and rows does not matter (makes no sense). Columns have no sub-columns (splits)</br>
2. 

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
