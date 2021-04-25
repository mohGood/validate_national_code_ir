### Validate National Code IR 

- a function for check national code (کد ملی) with PHP.
- Just pass your string to function.


####PHP　

```php
function check_national_code($code)
{
    if (!preg_match('/^[0-9]{10}$/', $code))
        return false;
    for ($i = 0; $i < 10; $i++)
        if (preg_match('/^' . $i . '{10}$/', $code))
            return false;
    for ($i = 0, $sum = 0; $i < 9; $i++)
        $sum += ((10 - $i) * intval(substr($code, $i, 1)));
    $ret = $sum % 11;
    $parity = intval(substr($code, 9, 1));
    if (($ret < 2 && $ret == $parity) || ($ret >= 2 && $ret == 11 - $parity))
        return true;
    return false;
}
```

###End