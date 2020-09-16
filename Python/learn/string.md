
{0:0.0f}

1. the first "zero" is the **field_name** (https://docs.python.org/2/library/string.html#format-string-syntax)<br/>

If it’s a number, it refers to a positional argument.<br/>
Example:
```
>>> print("{1:.2f} {0:.2f}".format(0.12, 0.34))
0.34 0.12
```

2. the second "zero" is the **width** (https://docs.python.org/2/library/string.html#format-specification-mini-language)<br/>

Example:
```
>>> print("{:8.2f}".format(1))
    1.00
>>> print("{:08.2f}".format(1))  # using padding numbers
00001.00
```

3. the third "zero" is the **precision** (https://docs.python.org/2/library/string.html#format-specification-mini-language)

