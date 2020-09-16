
## <a href="https://docs.python.org/3/library/string.html">Common string operations</a>

<hr>

### 1. <a href="https://docs.python.org/3/library/stdtypes.html#string-methods">string methods</a>

- str.<b>strip</b>([chars]): removing the leading and trailing characters

<hr>

### 2. <a href="https://docs.python.org/3/library/string.html#custom-string-formatting">string formatting</a>

{0:0.0f}

1. the first "zero" is the **field_name** (see <a href="https://docs.python.org/3/library/string.html#format-string-syntax">format string syntax</a>)<br/>
If it’s a number, it refers to a positional argument.<br/>
Example:
```
>>> print("{1:.2f} {0:.2f}".format(0.12, 0.34))
0.34 0.12
```

2. the second "zero" is the **width** (see <a href="https://docs.python.org/3/library/string.html#format-specification-mini-language">format specification mini-language</a><br/>
Example:
```
>>> print("{:8.2f}".format(1))
    1.00
>>> print("{:08.2f}".format(1))  # using padding numbers
00001.00
```

3. the third "zero" is the **precision**

