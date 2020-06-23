# PHP Notes

## Notes
__Remember Semicolons `;;;;;;;;;`__
(go brrrrrrrr)
### bool
- Each basic type has it's own rules for converting to bool

### strings
- single quote literals only allow escapes for `\'` and `\\`
- double quote literals allow variable embedding
- multiline strings without heredoc/nowdoc
```
echo 'You can also have embedded newlines in
strings this way as it is
okay to do';
```
- A table of double quote string escapes is [here](https://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.double)
- Heredoc strings exists, and work like double quote strings:
```
echo <<<EOT
My name is "$name". I am printing some $foo->foo.
Now, I am printing some {$foo->bar[1]}.
This should print a capital 'A': \x41
EOT;
```
- Nowdoc strings are 100% literal:
```
// note the single quotes around the identifier
echo <<<'EOD'
Example of string spanning multiple lines
using nowdoc syntax. Backslashes are always treated literally,
e.g. \\ and \'.
EOD;   
```
- Strings can be indexed like an array of characters

## Arrays
- Actually secretly an __ordered__ map
- Arrays are many purpose containers, doing the work of:
  - lists
  - hash tables/dictionaries
  - Stack (using [array_pop](https://www.php.net/manual/en/function.array-pop.php)
  and [array_push](https://www.php.net/manual/en/function.array-push.php))
- Literals like this:
```
$array = array(
    "foo" => "bar",
    "bar" => "foo",
);

// as of PHP 5.4
$array = [
    "foo" => "bar",
    "bar" => "foo",
];
```
- Array Key types are strange
  - Keys can be ints or strings. Values can be any type.
  - Keys of string type containing valid numbers are converted to int keys (wack)
  - Keys of float type are converted to int keys
  - Keys of bool type are converted to int keys (false = 0, true = 1)
  - Keys of `NULL` type are converted to the empty string `""` (very wack)
  - If something can't be used as a key, `Illegal offset type` warning is given

- Array literals with no keys use incrementing integers
- Array literals can mix elements with and without keys.
- Appending to arrays can be done like this: `$arr[] = value`


## Useful Tricks
- Float equality should be computed as follows:
```
<?php
$a = 1.23456789;
$b = 1.23456780;
$epsilon = 0.00001;

if(abs($a-$b) < $epsilon) {
    echo "true";
}
```

## Concerning Language Quirks
- `True` and `False` literals are case insensitive
- integer `-0` may exist? (referenced in booleans page)
- The string `"0"` is falsy
- Float `NAN` is truthy, but is not equal to any value
- Float `NAN` is not equal to itself (probably a good idea)
- Overflowing integers become floats automatically
- Dividing ints results in a float value
- float size and format is implementation specific
- No native unicode support
- Curly braces can be used for array access just the same 
as square braces, like this `$array[42]` and `$array[42]`

