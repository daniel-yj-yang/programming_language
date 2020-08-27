# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

## <a href="./Flow_Control.md">Flow Control</a>

### Clojure's ```for```

<hr>

Example:
- List comprehension, **not** a for-loop
- Generator function for sequence permutation
- Bindings behave like ```doseq```

```Clojure
user=> (for [letter [:a :b :c]
             number (range 4)] ;; list of 0, 1, 2, 3
         [letter number])
([:a 0] [:a 1] [:a 2] [:a 3] [:b 0] [:b 1] [:b 2] [:b 3] [:c 0] [:c 1] [:c 2] [:c 3])

user=> (for [letter [:a :b :c]
             number (range 4)] ;; list of 0, 1, 2, 3
         (prn [letter number]))
([:a 0]
[:a 1]
[:a 2]
[:a 3]
nil nil nil [:b 0]
[:b 1]
[:b 2]
[:b 3]
nil nil nil nil [:c 0]
[:c 1]
[:c 2]
[:c 3]
nil nil nil nil nil)
```

