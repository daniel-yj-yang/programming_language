
<a href="https://www.programiz.com/python-programming/decorator">Decorator</a> is meta-programming

<hr>

#### 1. Decorating Functions Without Arguments

Define the decorator first:

```python3
def decorate_without_arguments(func):
    def inner_working():
        print("-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=")
        return func()
    return inner_working
```

Then

```python3
@decorate_without_arguments
def this_is_a_func():
    print("Original function: I am doing something")
```

is equivalent to

```python3
def this_is_a_func():
    print("Original function: I am doing something")
this_is_a_func = decorate_without_arguments(this_is_a_func)
```

<hr>

Example:
```
this_is_a_func()
```

Output:
```
-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=
Original function: I am doing something
```

<hr>

#### 2. Decorating Functions With Arguments

Define the decorator first:

```python3
def decorate_with_arguments(func):
    def inner_working(arg1, arg2):
        print("-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=")
        print("arg1 = ", arg1)
        print("arg2 = ", arg2)
        return func(arg1, arg2)
    return inner_working
```

Then

```python3
@decorate_with_arguments
def this_is_an_addition_func(a, b):
    print("Original function: I am adding", a, "and", b)
    print("The answer is", a+b)
```

is equivalent to

```python3
def this_is_an_addition_func(a, b):
    print("Original function: I am adding", a, "and", b)
    print("The answer is", a+b)
this_is_an_addition_func = decorate_with_arguments(this_is_an_addition_func)
```

<hr>

Example:
```
this_is_an_addition_func(1, 2)
```

Output:
```
-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=
arg1 =  1
arg2 =  2
Original function: I am adding 1 and 2
The answer is 3
```

<hr>

#### 3. Decorating \*Any\* Function With \*General\* Arguments

More generally, using <b>\*args</b> (the tuple of positional arguments) and <b>\*\*kwargs</b> (the dictionary of keyword arguments) to decorate any function.

Define the decorator first:

```python3
def decorate_with_general_arguments(func):
    def inner_working(*args, **kwargs):
        print("-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=")
        print("arg1 = ", args[0])
        print("arg2 = ", args[1])        
        return func(*args, **kwargs)
    return inner_working
```

Then

```python3
@decorate_with_general_arguments
def this_is_an_addition_func(a, b):
    print("Original function: I am adding", a, "and", b)
    print("The answer is", a+b)
```

is equivalent to

```python3
def this_is_an_addition_func(a, b):
    print("Original function: I am adding", a, "and", b)
    print("The answer is", a+b)
this_is_an_addition_func = decorate_with_general_arguments(this_is_an_addition_func)
```

<hr>

Example:
```
this_is_an_addition_func(1, 2)
```

Output:
```
-=-=-=-=-=-=-=-=-= Decorating in action -=-=-=-=-=-=-=-=-=
arg1 =  1
arg2 =  2
Original function: I am adding 1 and 2
The answer is 3
```

<hr>

#### 4. The built-in <a href="https://docs.python.org/3/library/functions.html#property">`property()`</a> function and the `@property` decorator

First, the syntax ot the property class/function:
```python3
property(fget=None, fset=None, fdel=None, doc=None)
```
where,
- `fget` is an optional function argument to get value of the attribute, and can be specified by the method `getter()`
- `fset` is an optional function argument to set value of the attribute, and can be specified by the method `setter()`
- `fdel` is an optioal function argument to delete the attribute, and can be specified by the method `deleter()`
- `docs` is an optional string argument (like a comment)

Then

```python3
# using the property() class/function
class USD:
    def __init__(self, amount=0):
        print("Initializing...")
        self.amount = amount # this will invoke set_amount(), as specified by property()

    def to_TWD(self):
        return (self.amount * 30) # this will invoke get_amount(), as specified by property()

    # getter
    def get_amount(self):
        print("Original function: Getting amount from the private _amount variable")
        return self._amount

    # setter
    def set_amount(self, amount):
        print("Original function: Setting amount to be", amount, "and storing it in the private _amount variable")
        if amount < 0:
            raise ValueError("Amount cannot be below 0")
        self._amount = amount

    # creating a property object
    amount = property(fget = get_amount, fset = set_amount) # The amount attribute is now a property object which provides an interface to the private _amount variable. 
```

is equivalent to

```python3
# Using @property decorator
class USD:
    def __init__(self, amount=0):
        print("Initializing...")
        self.amount = amount # this will invoke USD.amount.setter(), as specified by property()

    def to_TWD(self):
        return (self.amount * 30) # this will invoke USD.amount.getter()

    @property # decorate the following retrieving amount() with property(), the default is to specify the getter() method, amount() is now a property() function
    def amount(self):
        print("Original function: Getting amount from the private _amount variable")
        return self._amount

    @amount.setter # decorate the following specifying amount() with the previous amount.setter() function
    def amount(self, amount):
        print("Original function: Setting amount to be", amount, "and storing it in the private _amount variable")
        if amount < 0:
            raise ValueError("Amount cannot be below 0")
        self._amount = amount
```

<hr>

Example:
```
savings = USD(100)
print(savings.to_TWD())
```

Output:
```
Initializing...
Original function: Setting amount to be 100 and storing it in the private _amount variable

Original function: Getting amount from the private _amount variable
3000
```
