without a trailing comma, a single-item tuple will be interpreted as a string.
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
