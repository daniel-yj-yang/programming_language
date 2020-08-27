
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

### REPL (Read-Eval-Print-Loop)

<hr>

#### 1. Exploring at the REPL

Clojure is always compiled to JVM bytecode before execution. There is no Clojure interpreter. 

<hr>

Use special symbols ```*n``` to represent the results of recent evaluations

- \*1 (the last result)
- \*2 (the result two expressions ago)
- \*3 (the result three expressions ago)

Example:
```Clojure
user=> (+ 5. 8.)
13.0
user=> (+ 17. *1)
30.0
user=> (+ *1 *2)
43.0
user=> (+ *1 *2 *3)
86.0
```

<hr>

To load the standard Clojure library:

```Clojure
(require '[clojure.repl :refer :all])
```

<hr>

Use ```doc``` to show documentations of functions

Example:
```Clojure
user=> (doc +)
-------------------------
clojure.core/+
([] [x] [x y] [x y & more])
  Returns the sum of nums. (+) returns 0. Does not auto-promote
  longs, will throw on overflow. See also: +'
nil

user=> (doc doc)
-------------------------
clojure.repl/doc
([name])
Macro
  Prints documentation for a var or special form given its name,
   or for a spec if given a keyword
nil
```

<hr>

Use ```apropos``` to find functions

Example:
```Clojure
user=> (apropos "+")
(clojure.core/+ clojure.core/+' clojure.core/read+string clojure.spec.alpha/+ clojure.spec.alpha/rep+impl)
```

<hr>

Use ```find-doc``` to search in the docstrings of functions

Example:
```Clojure
user=> (find-doc "infinity")
-------------------------
clojure.core/mod
([num div])
  Modulus of num and div. Truncates toward negative infinity.
-------------------------
clojure.core/range
([] [end] [start end] [start end step])
  Returns a lazy seq of nums from start (inclusive) to end
  (exclusive), by step, where start defaults to 0, step to 1, and end to
  infinity. When step is equal to 0, returns an infinite sequence of
  start. When start is equal to end, returns empty list.
-------------------------
clojure.spec.alpha/double-in
([& {:keys [infinite? NaN? min max], :or {infinite? true, NaN? true}, :as m}])
Macro
  Specs a 64-bit floating point number. Options:

    :infinite? - whether +/- infinity allowed (default true)
    :NaN?      - whether NaN allowed (default true)
    :min       - minimum value (inclusive, default none)
    :max       - maximum value (inclusive, default none)
nil
```

<hr>

Use ```dir``` to see a list of functions in a particular namespace

Example:
```Clojure
user=> (dir clojure.repl)
apropos
demunge
dir
dir-fn
doc
find-doc
pst
root-cause
set-break-handler!
source
source-fn
stack-element-str
thread-stopper
nil
```

<hr>

Use ```source``` to see the underlying source for any function

Example:
```Clojure
user=> (source +)
(defn +
  "Returns the sum of nums. (+) returns 0. Does not auto-promote
  longs, will throw on overflow. See also: +'"
  {:inline (nary-inline 'add 'unchecked_add)
   :inline-arities >1?
   :added "1.2"}
  ([] 0)
  ([x] (cast Number x))
  ([x y] (. clojure.lang.Numbers (add x y)))
  ([x y & more]
     (reduce1 + (+ x y) more)))
nil
```
