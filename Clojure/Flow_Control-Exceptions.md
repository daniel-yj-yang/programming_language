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

Example:
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

<hr>

#### 2. Throwing exceptions

Example:
```Clojure
user=> (try
  (throw (Exception. "something went wrong"))
  (catch Exception e (.getMessage e)))
"something went wrong"
```

<hr>

#### 3. Exceptions with Clojure data

- ```ex-info``` takes a message and a map
- ```ex-data``` gets the map back out, or ```nil``` if not created with ```ex-info```

Example:
```Clojure
user=> (try
  (throw (ex-info "There was a problem" {:detail 42}))
  (catch Exception e
    (prn (:detail (ex-data e)))))
42
nil
```

<hr>

#### 4. ```with-open```

Example:
```Clojure
user=> (let [f (clojure.java.io/writer "/tmp/new")]
  (try
    (.write f "some text")
    (finally
      (.close f))))
nil

;; Can be written:
user=> (with-open [f (clojure.java.io/writer "/tmp/new")]
  (.write f "some text"))
nil
```
