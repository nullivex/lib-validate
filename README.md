openlss/lib-validate
============

Validation helper with a shorthand syntax.

Usage
----
```php
use \LSS\Validate;

$data = array('myparam'=>'valid string');

try {
	Validate::prime($data);
	Validate::go('myparam')->not('blank')->max(20)->is('alnum');
	Validate::paint();
} catch(Exception $e){
	echo $e;
}
```

Types
----
All these types will evaluate to true IF:
  * blank		'' === true
  * empty		empty() === true
  * null		is_null($var)
  * ip			var is IPv4 octect format
  * mac			True if var is in mac address format (loose check for chars)
  * domain		True if var is a domain name (loose check for chars)
  * num			True if var is all numeric
  * dec			True if the var is numeric with a decimal point
  * float		Same as dec
  * alpha		True if all characters are alpha-numeric
  * al			Same as alpha
  * alu			Same as alpha but with underscores (_)
  * als			True if var is alphanumeric with spaces
  * alnums		Alias to als
  * en			Alias to als
  * email		True if chars are valid for an email address
  * sha1		True if var is a sha1 hash
  * md5			True of var is a md5 hash 

Reference
----

### (void) Validate::prime($data)
Prep validate with an array of data usualy from post()

### (object) Validate::go($var)
Starts a validation object for the given param

### (object) Validate::_get()
Returns the current instance

### (object) Validate::error($err)
Add error message to buffer
This is generally used internally

### (object) Validate::setVar($var)
Sets the var to operate on 
This is generally used internally

### (string) Validate::get()
Retrieves the current variable
This is generally used internally

### (object) Validate::min($min)
Checks that the current var is at minimum $min long

### (object) Validate::max($max)
Checks that the current var is at maximum $max long

### (object) Validate::not($type)
Checks that the current var is not given $type

### (object) Validate::is($type)
Checks that the current var is given #type

### (bool) Validate::paint()
If there are any errors in the buffer an exception will be raised
Otherwise TRUE is returned

