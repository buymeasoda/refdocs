# PHP

## PHP Information

Show installed PHP version

    php -v

List active compiled php modules

    php -m

Show php configuration and environment information

    php -i

## Run Script

Manually execute a PHP script

    php -q <script>

## PHP Interactive Shell

Start interactive shell from the command line

    php -a

Exit interactive shell

    quit
    CTRL+C

## Simple PHP Server

Start a server in the current directory

    php -S localhost:8000

## Output Strings

Output a string or formatted string

    echo $var
    print($var)
    printf($format, $value)

Output readable/detailed debugging information about a variable

    print_r($var)
    var_dump($var)

Output valid php code that describes the variable

    var_export($var)

## Introspection

### Class Introspection

Get declared classes, traits and interfaces

    get_declared_classes()
    get_declared_traits()
    get_declared_interfaces()

Get defined vars, constants and functions

    get_defined_vars()
    get_defined_constants()
    get_defined_functions()

Check if a class exists

    class_exists($class_name)

Get the parent classes, interfaces and traits a class uses

    class_parents($class_name_or_instance)
    class_implements($class_name_or_instance)
    class_uses($class_name_or_instance)

Get parent class, methods or vars from a class

    get_parent_class($class_name_or_instance)
    get_class_methods($class_name_or_instance)
    get_class_vars($class_name)

### Object Introspection

Test for an object and get the class an object belongs to

    is_object($object)
    get_class($object)

Check if a method or property exists on an object

    method_exists($object, $method_name)
    property_exists($object, $property_name)

Get object vars and object parent class

    get_object_vars($object)
    get_parent_class($object)

Get the type of a variable

    gettype($var)

Test if an object is a particular class

    is_a($object, $class_name)
    $object instanceof $class

### Array Introspection

Output array keys

    array_keys($array)

Typecast object to array and output list of keys

    print_r(array_keys((array)$object))
