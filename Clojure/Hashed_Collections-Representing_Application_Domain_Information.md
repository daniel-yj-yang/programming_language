# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

### Representing Application Domain Information

<hr>

To represent domain information with the same set of fields, use a map with keyword keys.

Example:
```Clojure
user=> (def person
  {:first-name "Donald"
   :last-name "Trump"
   :age 74
   :occupation "President"})
#'user/person

user=> (:occupation person) ;; to access field values by invoking the keyword as functions
"President"

user=> (assoc person :occupation "President-Candidate") ;; to modify field
{:first-name "Donald", :last-name "Trump", :age 74, :occupation "President-Candidate"}

user=> (dissoc person :age) ;; to remove field
{:first-name "Donald", :last-name "Trump", :occupation "President"}

;; Nested entities
user=> (def place
{:name "The White House"
:addr {:street "1600 Pennsylvania Avenue NW"
:city "Washington"
:state "DC"
:zipcode "20500" }})
#'user/place

;; access
user=> (get-in place [:addr :zipcode])
"20500"

;; update
user=> (assoc-in place [:addr :state] "District of Columbia")
```

<hr>

