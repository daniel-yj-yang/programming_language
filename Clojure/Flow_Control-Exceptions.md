# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

## <a href="./Flow_Control.md">Flow Control</a>

### Exceptions

<hr>

#### 1. Exception handling

```try```/```catch```/```finally``` as in Java

```Clojure
user=> (try
  (/ 2 1)
  (catch ArithmeticException e
    "divide by zero")
  (finally
    (println "cleanup")))
cleanup
2
```


