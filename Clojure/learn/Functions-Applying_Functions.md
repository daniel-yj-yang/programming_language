
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

### Applying Functions

<hr>

#### 1. ```apply```

The ```apply``` function invokes a function with 0 or more fixed arguments, and draws the rest of the needed arguments from a final list/sequence. This helps shorten the code, making it more elegant.

Instead of writing this:
```Clojure
(defn plot [shape coords]
  (plotxy shape (first coords) (second coords)))
```

Write this:
```Clojure
(defn plot [shape coords]
  (apply plotxy shape coords))
```
