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

Example:
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

user=> (temperature "2020-08-28" 80) ;; Looking up with a default; useful when the key is not found
80

user=> (contains? temperature "2020-08-27") ;; Checking contains
true

user=> (find temperature "2020-08-27") ;; Checking contains
["2020-08-27" 88]

user=> (keys temperature) ;; Keys, sequential order
("2020-08-25" "2020-08-26" "2020-08-27")

user=> (vals temperature) ;; Values, sequential order
(92 80 88)

user=> (zipmap ["2020-08-27" "2020-08-26" "2020-08-25"] [88 80 92]) ;; build a map by zipping together two sequences
{"2020-08-27" 88, "2020-08-26" 80, "2020-08-25" 92}

user=> (into {} (map (fn [player] [player 0]) players)) ;; build a map by using map and into (this topic should be revisited later)
{"Alpha" 0, "Charlie" 0, "Bravo" 0, "Sigma" 0}

user=> (reduce (fn [m player] ;; build a map by using reduce (this topic should be revisited later)
          (assoc m player 0))
        {} ; initial value
        players)
{"Alpha" 0, "Charlie" 0, "Bravo" 0, "Sigma" 0}

user=> (merge temperature {"2020-08-24" 95 "2020-08-23" 92}) ;; merging maps; if both maps contain the same key, the rightmost one wins.
{"2020-08-25" 92, "2020-08-26" 80, "2020-08-27" 88, "2020-08-24" 95, "2020-08-23" 92}

;; see also merge-with that resolves conflict in merging maps

user=> (def sm (into (sorted-map) temperature)) ;; Sorted maps
#'user/sm

user=> sm
{"2020-08-25" 92, "2020-08-26" 80, "2020-08-27" 88}
```
