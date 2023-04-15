# PHP Accessors

Define getter and setter for inaccessible members of a PHP class

# Installation

`composer require himanshu-m/accessors`

# Usage

Use the trait in any class to build getter and/or setters for the private and protected properties of the classes. It can also allow instance method which do not accept any arguments to invoked just like using a property of the object.

```php
use Accessors;

class AccessorsTest
{
    use Accessors;

    private string $prop1;
    private string $prop2;

    function __construct(string $p1, string $p2)
    {
	$this->prop1 = $p1;
	$this->prop2 = $p2;

	$this->acccessible("prop1");
	// prop2 can also be renamed as readonlyProp for access from outside.
	$this->readonly("readonlyProp", "prop2");
    }
}

$obj = new AccessorsTest("property1", "property2");

echo $obj->prop1;
// property1
$obj->prop1 = "changed prop1";
echo $obj->readonlyProp;
// property2
$obj->readonlyProp = "cannot change prop2...";
// Exception: Property 'readonlyProp' of class AccessorsTest is not accessible
```
