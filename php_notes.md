
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


