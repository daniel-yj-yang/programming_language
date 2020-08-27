
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

### Vectors

<hr>

Vectors are represented with ```[ ]```, like ```[4 5 6]```

#### 1. Indexed access

indexes start at 0, not 1. Use the get function to retrieve an element at an index.

```Clojure
user=> (get ["2020" true 827] 0) 
"2020"

user=> (get ["2020" true 827] 1) 
true

user=> (get ["2020" true 827] 3) ;; invalid index
nil
```

<hr>

#### 2. Count

```Clojure
user=> (def x ["Mon" "Tue" "Wed" "Thu" "Fri"])
#'user/x

user=> (count x)
5
```

<hr>

#### 3. Constructing

```Clojure
user=> ["Mon" "Tue" "Wed" "Thu" "Fri"]
["Mon" "Tue" "Wed" "Thu" "Fri"]

user=> (vector "Mon" "Tue" "Wed" "Thu" "Fri") ;; Alternative way to create a vector
["Mon" "Tue" "Wed" "Thu" "Fri"]
```

<hr>

#### 4. Adding elements

```Clojure
user=> (conj ["Mon" "Tue" "Wed" "Thu" "Fri"] "Sat" "Sun") ;; conjoin elements at the tail
["Mon" "Tue" "Wed" "Thu" "Fri" "Sat" "Sun"]
```

<hr>

#### 5. Immutability

```Clojure
user=> (def v (vector 1 2 3 4 5))
#'user/v

user=> (conj v 6 7)
[1 2 3 4 5 6 7]

user=> v
[1 2 3 4 5]
```
