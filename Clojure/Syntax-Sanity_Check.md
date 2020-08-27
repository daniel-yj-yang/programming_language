
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

### Sanity Check

<hr>

#### 1. Using the REPL, compute the sum of 5678 and 3210.

Answer:
```Clojure
user=> (+ 5678 3210)
8888
```

<hr>

#### 2. Rewrite the following algebraic expression as a Clojure expression: ( 8 + 2 * 8 + 10 ) / 5.

Answer:
```Clojure
user=> (/ (+ 8 (* 2 8) 10) 5)
34/5
```

<hr>

#### 3. Using REPL documentation functions, find the documentation for the rem and mod functions.

Answer:
```Clojure
user=> (doc rem)
-------------------------
clojure.core/rem
([num div])
  remainder of dividing numerator by denominator.
nil

user=> (doc mod)
-------------------------
clojure.core/mod
([num div])
  Modulus of num and div. Truncates toward negative infinity.
nil
```

<hr>

#### 4. Using find-doc, find the function that prints the stack trace of the most recent REPL exception.

Answer:
```Clojure
user=> (find-doc "a stack trace of")
-------------------------
clojure.repl/pst
([] [e-or-depth] [e depth])
  Prints a stack trace of the exception, to the depth requested. If none supplied, uses the root cause of the
  most recent repl exception (*e), and a depth of 12.
nil
```
