# PHP Notes

## Notes
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
