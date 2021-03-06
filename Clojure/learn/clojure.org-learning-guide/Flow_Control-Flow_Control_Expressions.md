# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

## <a href="./Flow_Control.md">Flow Control</a>

### Flow Control Expressions

<hr>

Example:
```Clojure
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; if

user=> (def x 1230132)
#'user/x

user=> (str x " is " (if (even? x) "even" "odd")) ;; if, the conditional expression
"1230132 is even"

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; truth

user=> (if true :true :false)
:true

user=> (if [] :true :false)
:true

user=> (if 0 :true :false)
:true

user=> (if false :true :false) ;; In Clojure, the only "false" values are false and nil 
:false

user=> (if nil :true :false) ;; In Clojure, the only "false" values are false and nil 
:false

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; if and do ;; the only reason to do this is if the bodies have side effects

user=> (if (even? x)
  (do (println "even") ;; Use do to create larger blocks that are a single expression.
      true)
  (do (println "odd")
      false))
even
true

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; when ;; it checks a condition and then evaluates any number of statements as a body (so no do is required).
;; The value of the last expression is returned. If the condition is false, nil is returned.

user=> (when (even? x)
  (throw (RuntimeException. (str "x must be even: " x))))
Execution error at user/eval194 (REPL:2).
x must be even: 1230132

user=> (when (odd? x)
  (throw (RuntimeException. (str "x must be even: " x))))
nil

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; cond (like switch in R) is a series of tests and expressions.
;; Each test is evaluated in order and the expression is evaluated and returned for the first true test.
;; If no test is satisfied, nil is returned.
;; Keywords (like :else) always evaluate to true so this will always be selected as a default.

user=> (cond
    (< x 2) "x is less than 2"
    (< x 10) "x is less than 10"
    :else "x is some value else")
"x is some value else"

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; case is similar to cond, except that it will throw an exception if no value matches.

user=> (defn foo [x]
(case x
10 "x is 10"
20 "x is 20"))
#'user/foo

user=> (foo 10)
"x is 10"

user=> (foo 50)
Execution error (IllegalArgumentException) at user/foo (REPL:2).
No matching clause: 50

user=> (defn foo [x] ;; an else expression can be added too
(case x
10 "x is 10"
20 "x is 20"
"x isn't 10 or 20"))
#'user/foo

user=> (foo 50)
"x isn't 10 or 20"
```
