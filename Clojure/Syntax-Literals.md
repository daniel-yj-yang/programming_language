
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

### Literals

<hr>

#### 1. Numeric types

```Clojure
84        ; integer
-3.14     ; floating point
31/9      ; ratio
##Inf     ; positive infinity
##-Inf    ; negative infinity
##NaN     ; "not a number" 
```

Examples:
```Clojure
user=> (/ 1 ##Inf)
0.0
user=> (/ ##Inf ##Inf)
##NaN
```

<hr>

#### 2. Character types

```Clojure
"heythere"         ; string
\n                 ; character
#"[0-9a-z]+"       ; regular expression
```

<hr>

#### 3. Symbols and keywords

```Clojure
map             ; symbol
+               ; symbol - most punctuation allowed
clojure.core/+  ; namespaced symbol
nil             ; null value
true false      ; booleans
:alpha          ; keyword
:release/alpha  ; keyword with namespace
```

<hr>

#### 4. Literal collections

```Clojure
'(4 5 6)      ; list, delaying evaluation with quoting '
[4 5 6]       ; vector
#{4 5 6}      ; set
{:a 4, :b 5}  ; map
```
