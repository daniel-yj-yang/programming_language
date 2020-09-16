without a trailing comma, a single-item <a href="https://docs.python.org/3.3/library/stdtypes.html?highlight=tuple">tuple</a> will be interpreted as a string.
```
>>> a = ('foo')
>>> type(a)
<class 'str'>
```

with a trailing comma, a single-item tuple will be correctly interpreted as a tuple.
```
>>> a = ('foo',)
>>> type(a)
<class 'tuple'>
```

<hr>

For a multiple-item tuple, the trailing comma is <a href="https://stackoverflow.com/questions/7992559/what-is-the-syntax-rule-for-having-trailing-commas-in-tuple-definitions">a good practice for style reason</a>.
