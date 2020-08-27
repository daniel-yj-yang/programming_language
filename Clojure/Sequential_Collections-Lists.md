
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

### Lists

<hr>

#### 1. Constructing

```Clojure
user=> (def cards '(2 :club 2 :diamond 2 :heart 2 :spade))        
#'user/cards

user=> (first cards) ;; list is not indexed and must be retrieved using first, last, rest
2

user=> (last cards)
:spade

user=> (rest cards) ;; list is not indexed and must be retrieved using first, last, rest
(:club 2 :diamond 2 :heart 2 :spade)

user=> cards
(2 :club 2 :diamond 2 :heart 2 :spade)
```

<hr>

#### 2. Adding elements

```Clojure
user=> (conj cards 3 :club)
(:club 3 2 :club 2 :diamond 2 :heart 2 :spade) ;; for a list, elements are added at the head
```

<hr>

#### 3. Stack access

```Clojure
user=> (peek cards) ;; for a list, same as first
2

user=> (pop cards)  ;; for a list, same as rest
(:club 2 :diamond 2 :heart 2 :spade)
```
