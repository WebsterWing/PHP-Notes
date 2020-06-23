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
