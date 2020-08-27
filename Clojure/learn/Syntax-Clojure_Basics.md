
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

### Clojure Basics

<hr>

#### 1. ```def```

Associate a symbol with a constant or a function.

Example:
```Clojure
user=> (def x 99)
#'user/x

user=> (+ x 1)
100
```

<hr>

#### 2. printing

&nbsp; | With newline | Without newline
--- | --- | ---
For humans | ```println``` | ```print```
Readable as data | ```prn``` | ```pr```

Example (note that quotation mark difference):
```Clojure
user=> (prn "1+2 =" (+ 1 2))
"1+2 =" 3
nil

user=> (println "1+2 =" (+ 1 2))
1+2 = 3
nil
```
