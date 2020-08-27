# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

### Maps

Two functions:
1. to manage an association of keys to values (namely, dictionaries)
2. to represent domain application data

<hr>

```Clojure
user=> (def temperature {"2020-08-25" 92 "2020-08-26" 80 "2020-08-27" 88}) ;; Creating a literal map by { and }.
#'user/temperature

user=> temperature
{"2020-08-25" 92, "2020-08-26" 80, "2020-08-27" 88}

user=> (assoc temperature "2020-08-20" 100) ;; Adding a new key-value pair, or updating it
{"2020-08-25" 92, "2020-08-26" 80, "2020-08-27" 88, "2020-08-20" 100}

user=> (dissoc temperature "2020-08-20") ;; Removing a key-value pair
{"2020-08-25" 92, "2020-08-26" 80, "2020-08-27" 88}

user=> (get temperature "2020-08-27") ;; Looking up by key
88

user=> (temperature "2020-08-27") ;; Looking up by key
88

user=> (temperature "2020-08-28")
nil
```

