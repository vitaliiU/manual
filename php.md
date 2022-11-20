# PHP Manual

## Content

- [Generalinfo](#Genera_info)
- [PHPTags](#PHPTags)
- [DataTypeVariables](#DataTypeVariables)
- [References](#References)
- [RequireInclude](#RequireInclude)
- [Function](#Function)
- [Array](#Array)

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
- [Scope&&Argument](#Scope&&Argument)

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

//we can use outer variable by use "function () use ($arg)" in function-expretion
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


## Array

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
