
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

### Locals and Closures

<hr>

#### 1. ```let```

```let``` creates local (temporary) bindings for names and the names take precedence over the names in the outer (global) context.

In the code below, ```a```, ```b```, and ```c``` have no meaning outside the lexical scope created by ```let```
```Clojure
user=> (defn my_func [msg]
  (let [a 15
        b 20
        c (clojure.string/capitalize msg)]
    (println a b c)
  ) ;; end of let scope
) ;; end of function
#'user/my_func

user=> (my_func "abc")
15 20 Abc
nil
```

<hr>

#### 2. Closures

To avoid the use of global values, we can **enclose data in a function** (called 'closure') when the function is created, and the data can still be accessed out of the lexical scope.

Requirements:
- Need to build a nested function
- The nested function needs to use a value defined in the enclosing function
- The enclosing function needs to return the nested function
- Need to use the special form ```fn``` to build the nested function

```Clojure
user=> (defn make_multiplier_of [n]
  (fn [x] (* x n)))
#'user/make_multiplier_of

;;  when created, the function times3 has the value 3 enclosed in (attached to) the function
user=> (def times3 (make_multiplier_of 3)) 
#'user/times3

;;  when created, the function times5 has the value 5 enclosed in (attached to) the function
user=> (def times5 (make_multiplier_of 5)) 
#'user/times5

user=> (times3 9) ;; 3 is now out of scope but still accessible as it's enclosed in the function
27

user=> (times5 3) ;; 5 is now out of scope but still accessible as it's enclosed in the function
15

user=> (times5 (times3 2))
30
```
