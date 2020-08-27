# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

## <a href="./Flow_Control.md">Flow Control</a>

### Iteration for Side Effects

<hr>

#### 1. dotimes (do times)

- Evaluate expression <i>n</i> times
- Returns nil

```Clojure
user=> (dotimes [i 10]
         (println i))
0
1
2
3
4
5
6
7
8
9
nil
```

<hr>

#### 2. doseq (do sequence)

- Iterates over a sequence
- Returns nil

```Clojure
user=> (doseq [n (range 10)]
         (println n))
0
1
2
3
4
5
6
7
8
9
nil
```
