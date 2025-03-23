
### PHP Notes 

##### Basic Syntax
```php
<?php 

?>
```

##### Basic example with html 
```
<!DOCTYPE html> 
<html> 
	<title>PHP in HTML</title>
<head> 
</head> 
<body>
	<h1><?php PHP in HTML ?> </h1>
</body>
</html>
```

##### PHP version 
```
[tamr@devbox ~]$ php --version
PHP 8.2.12 (cli) (built: Nov 25 2023 08:09:53) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.2.12, Copyright (c) Zend Technologies
```

##### Running PHP on command line 
``` 
<?php
echo "This is php on command"; // CTRL + D  
?>

##### NOT case sensitive 
- In PHP below things are not case sensitive 
   - keywords  
   - classes 
   - functions 
   - user-defined functions 
- ECHO is the same as echo 
- However **variable names are case sensitive** 

##### Two types of commands 
- single line // 
- multi line commands /*  */

##### PHP variables 
- in php variable starts with the $ sign  
  $x = 10;
  $y = y; 
- it is good practice to give variable a descriptive name 
- variable name starts with a $ 
- variable name must start with character or underscore 
- variable name cannot start with a number (X) 
- variable name can only contain alpha-numeric characters and underscore A-Z,0-9, _ 
- Variable names are case sensitive 

##### String concatination 
- . is used to concatenate the string 
```php 

$num1 = 10;
$num2 = 20;
$total = $num1 + $num2;

echo "The sum is {total}\n";

#END
```

##### Data types 
- String 
- Boolean 
- Integer 
- Float 
- Array 
- NULL 
- Resource 

```php 
#!/usr/bin/env php

<?php
//String
$var_str = 'String Var';
//Integer
$var_int = 123;
//Float
$var_flt = 12.40;
//Boolean
$var_bol = true;
//Array
$var_arr = ['apple','pear','banana'];
//NULL
$var_empty;
//Undefined

echo "String variable: ${var_str}\n";
echo "Integer variable: ${var_int}\n";
echo "Float variable: ${var_flt}\n";
echo "Boolean variable: ${var_bol}\n";
echo "Array variable:\n";
print_r($var_arr);
?>
```

##### Var dump 
```php 
#!/usr/bin/env php

<?php
//String
$var_str = 'String Var';
//Integer
$var_int = 123;
//Float
$var_flt = 12.40;
//Boolean
$var_bol = true;
//Array
$var_arr = ['apple','pear','banana'];
//NULL
$var_empty;
//Undefined

echo "String variable: ${var_str}\n";
var_dump($var_str);
echo "Integer variable: ${var_int}\n";
var_dump($var_int);
echo "Float variable: ${var_flt}\n";
var_dump($var_flt);
echo "Boolean variable: ${var_bol}\n";
var_dump($var_bol);
echo "Array variable:\n";
print_r($var_arr);
var_dump($var_arr);

// assign value to a variable ex. string
$str_var = "Hello".PHP_EOL;
echo $str_var;

// assign multiple value to a string
$a = $b = $c = "Fruit";
echo $a.PHP_EOL;
echo$b.PHP_EOL;
echo $c.PHP_EOL;
?>

```

##### Local / global variable 
```php
#!/usr/bin/env php
<?php
#
#
#

$x = 5;

function myTest(){
        $x = 10;
        echo "X inside the function is: ${x} value \n";
}

echo "X outside the function has: ${x} value \n";
myTest();

#END
?>
```

- output: 
```
$ php 06_local_global_variables.php
X outside the function has: 5 value
X inside the function is: 10 value
```

##### GLOBALS array 
```php 
#
#GLOBALS array usage for global
#

$x = 5;
$y = 10;

function myTest(){

        $GLOBALS['y'] = $GLOBALS['x'] + 10;
}

myTest();
echo $y;
```

##### static variable 
```php 
#!/usr/bin/env php
#
<?php

function myTest() {
        static $x = 0;
        echo $x;
        echo "\n";
        $x++;
}

myTest();
myTest();
myTest();
myTest();
myTest();

?>
```

##### Array basic 
OUTPUT
```php 
Array
(
    [0] => volvo
    [1] => toyota
    [2] => honda
)
Array
(
    [0] => Apple
    [1] => 23
    [2] => Sweets
)
```
CODE
```
#!/usr/bin/env php
#
<?php

        $cars = array("volvo","toyota","honda");
        $fruits = ['Apple',23,'Sweets'];

        print_r($cars);
        print_r($fruits);



?>
```

##### classes and objects 
- Classes and objects are two main aspects of oop 
- class is a template of objects 
- __construct is a constructor function that run automatically. 

```php 
#!/usr/bin/env php
#
<?php

class Car {
        public $color;
        public $model;
        public function __construct($color, $model) {
                $this->color = $color;
                $this->model = $model;
        }

        public function message() {
                return "My car is a ". $this->color . " " . $this->model . "!";
        }

}

$myCar = new Car("red","Volvo");
```

OUTPUT 
```
object(Car)#1 (2) {
  ["color"]=>
  string(3) "red"
  ["model"]=>
  string(5) "Volvo"
}
```

##### Dynamic Change of data type  
- if you assign a value like 5 the variable will be integer 
- if you assign the same variable another value like 'apple' the type will auto change. 

- if you want to change the type of the variable but not the value you can use casting. 
```php 
$ cat 12_type_casting.php
#!/usr/bin/env php
#
<?php

$x = 5;
$x = (string) $x;
var_dump($x);


?>
```

OUTPUT 
```
#
string(1) "5"
```

############################## W3Schools ########################


### First Sample 
```php 
<!DOCTYPE html>
<html>
<body>
 
<?php
echo "My first PHP script!";
?>

</body>
</html>
```

### Pre-requisite 
What You Should Already Know
Before you continue you should have a basic understanding of the following:

- HTML
- CSS
- JavaScript

### What is PHP 
- PHP is an acronym for "PHP: Hypertext Preprocessor"
- PHP is a widely-used, open source scripting language
- PHP scripts are executed on the server
- PHP is free to download and use

### What PHP can do PHP can generate dynamic page content
- PHP can create, open, read, write, delete, and close files on the server
- PHP can collect form data
- PHP can send and receive cookies
- PHP can add, delete, modify data in your database
- PHP can be used to control user-access
- PHP can encrypt data

### PHP editor
```
<?php
$txt = "PHP";
echo "I love $txt!";
?>
```

### PHP version 
```
echo phpversion();
```

### Basic syntax 
```
<?php
// PHP code goes here
?>
```

- Note: PHP statements end with a semicolon (;).

### PHP Case Sensitivity
- In PHP, keywords (e.g. if, else, while, echo, etc.), classes, functions, and user-defined functions are not case-sensitive.
```
<!DOCTYPE html>
<html>
<body>

<?php
ECHO "Hello World!<br>";
echo "Hello World!<br>";
EcHo "Hello World!<br>";
?>

</body>
</html>
```

- Note: However; all variable names are case-sensitive!
- $COLOR is not same as $color

### Comments in PHP 
Comments can be used to:

- Let others understand your code
- Remind yourself of what you did - Most programmers have experienced coming back to their own work a year or two later and having to re-figure out what they did. Comments can remind you of what you were thinking when you wrote the code
- Leave out some parts of your code

```
// This is a single-line comment

# This is also a single-line comment

/* This is a
multi-line comment */
```

### PHP Variables 
- In PHP, a variable starts with the $ sign, followed by the name of the variable
- Note: When you assign a text value to a variable, put quotes around the value.
- Note: Unlike other programming languages, PHP has no command for declaring a variable. It is created the moment you first assign a value to it.

##### Rules for PHP variables:

- A variable starts with the $ sign, followed by the name of the variable
- A variable name must start with a letter or the underscore character
- A variable name cannot start with a number
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
- Variable names are case-sensitive ($age and $AGE are two different variables)
- Remember that PHP variable names are case-sensitive!

### Output Variables
The PHP echo statement is often used to output data to the screen.

``` 
$txt = "W3Schools.com";
echo "I love $txt!";
```
- Below and Above both have the same output 
```
$txt = "W3Schools.com";
echo "I love " . $txt . "!";
```

- Below will produce the calculation of two numbers 
```
$x = 5;
$y = 4;
echo $x + $y;
```

### PHP is a Loosely Typed Language
- PHP automatically associates a data type to the variable, depending on its value. Since the data types are not set in a strict sense, you can do things like adding a string to an integer without causing an error.
- In PHP 7, type declarations were added. This gives an option to specify the data type expected when declaring a function, and by enabling the strict requirement, it will throw a "Fatal Error" on a type mismatch.

##### Variable Types 
```
$x = 5;      // $x is an integer
$y = "John"; // $y is a string
echo $x;
echo $y;
```

##### Supported Data types 
PHP supports the following data types:

- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object
- NULL
- Resource



























