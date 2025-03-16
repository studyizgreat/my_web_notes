
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

