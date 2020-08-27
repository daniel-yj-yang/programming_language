
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

### Creating Functions

<hr>

#### 1. ```defn``` defines a named function

name: a single name
params: any number of parameters

```Clojure
;;    name   params         body
;;    -----  ------------  ---------------------------------------------
(defn add    [arg1, arg2]  (str arg1, " + ", arg2, " = " (+ arg1 arg2)))
```

Example:
```Clojure
user=> (defn add [arg1, arg2] (str arg1, " + ", arg2, " = " (+ arg1 arg2)))
#'user/add

user=> (add 1 2)
"1 + 2 = 3"
```

<hr>

#### 2. Multi-<a href="https://en.wikipedia.org/wiki/Arity">arity</a> functions

Function can take different numbers of arguments

```Clojure
user=> (defn add 
([]          (str "Not enough arg!")) 
([arg1]      (str "Still not enough arg!")) 
([arg1 arg2] (+ arg1 arg2)))
#'user/add

user=> (add)
"Not enough arg!"

user=> (add 1)
"Still not enough arg!"

user=> (add 1 2)
3
```

<hr>

#### 3. Variadic (remaining argument) functions

The variable at the end, if preceded by '&', will collect all remaining arguments.

```Clojure
user=> (defn show [the_first_arg & the_remaining_arg] 
(str "The first arg = ", the_first_arg, " ; the remaining arg = ", the_remaining_arg))
#'user/show

user=> (show "important" "information" "enclosed")
"The first arg = important ; the remaining arg = (\"information\" \"enclosed\")"
```

<hr>

#### 4. Anonymous Functions


Use ```fn``` instead of ```defn```, and pass to another function, as it cannot be referred later.

```Clojure
user=> (  (fn [message] (println message))  "Important Information" )
Important Information
nil
```

<hr>

#### 5. ```defn``` vs. ```fn```

```fn``` defines a function and ```def``` binds it to a name, so they togehter are equivalent to ```defn```

<hr>

#### 6. Anonymous function syntax using ```#()```

- % is used for a single argument
- %1, %2, %3, etc are used for multiple arguments
- %& is used for any remaining arguments

```Clojure
;; #(+ 10 %) is equivalent to: (fn [x] (+ 10 x))
user=> ( #(+ 10 %) 5 )
15

;; #(- %1 %2) is equivalent to: (fn [a b] (- a b))
user=> ( #(- %1 %2) 10 5 )
5

;; #(println %1 %2 %&) is equivalent to: (fn [a b & others] (println a b others))
user=> ( #(println %1 %2 %&) 1 2 3 4 5 )
1 2 (3 4 5)
```

<hr>

#### 7. Caveat

To take an element (or elements) and wrap it in a vector in an anonymous function, do the following:
```Clojure
user=> ( (fn [x] [x]) 123 )
[123]

user=> ( #(vector %&) 4 5 6 )
[(4 5 6)]
```
