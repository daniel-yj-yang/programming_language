# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

### Sets

<hr>

Sets are like math sets - unordered and with no duplicates.

Example:
```Clojure
user=> (def seasons #{"Winter" "Fall" "Spring"})  ;; or, (def seasons #{"Winter", "Fall", "Spring"}), as comma is treated as whitespace in Clojure
#'user/seasons

user=> seasons
#{"Spring" "Fall" "Winter"}

user=> (def seasons (conj seasons "Summer"))  ;; adding an item to a set
#'user/seasons

user=> seasons
#{"Spring" "Fall" "Summer" "Winter"}

user=> (def seasons (conj seasons "Summer" "Hot"))  
#'user/seasons

user=> seasons
#{"Spring" "Fall" "Summer" "Hot" "Winter"}

user=> (disj seasons "Hot")  ;; removing an item from a set
#{"Spring" "Fall" "Summer" "Winter"}

user=> (contains? seasons "Fall")  ;; Checking containment
true

user=> (into seasons #{"Cold" "Autumn"})    ;; putting another collection into the first one, returning collection of the same type as the first argument
#{"Cold" "Spring" "Fall" "Summer" "Hot" "Winter" "Autumn"}

user=> (apply sorted-set seasons)    ;; sorted-set
#{"Fall" "Hot" "Spring" "Summer" "Winter"}

user=> (sorted-set 3 1 2)    ;; sorted-set
#{1 2 3}

user=> (conj (sorted-set) "Z" "A" "M" "G" "W")    ;; sorted-set
#{"A" "G" "M" "W" "Z"}
```

