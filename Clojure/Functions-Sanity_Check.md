
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

### Sanity Check

<hr>

#### 1. Define a function ```recommend_movie``` that takes no arguments and prints "Star Wars", with the implementation: ```(defn recommend_movie [] ___)```.

Answer:
```Clojure
user=> (defn recommend_movie []
  (println "Star Wars"))
#'user/recommend_movie

user=> (recommend_movie)
Star Wars
nil
```

<hr>

#### 2. Redefine ```recommend_movie``` using ```def```, first with the ```fn``` special form and then with the ```#()``` reader macro.

Answer:
```Clojure
;; using fn
(def recommend_movie
  (fn [] (println "Star Wars")))

;; using #()
(def recommend_movie
  #(println "Star Wars"))
```

<hr>

#### 3. Define a function ```recommend_movie``` that:

- Given no arguments, returns "Try StarWars!"
- Given one argument x, returns "Try x!"
- Given two arguments x and y, returns "x y!"

Answer:
```Clojure
user=> (defn recommend_movie
  ([] (recommend_movie "Try" "StarWars"))
  ([x] (recommend_movie "Try" x))
  ([x y] (str x ", " y "!")))  ;; use the str function to concatenate strings
#'user/recommend_movie

user=> (recommend_movie)
"Try, StarWars!"

user=> (recommend_movie "ToyStory")
"Try, ToyStory!"

user=> (recommend_movie "Try" "Aladdin")    
"Try, Aladdin!"
```

<hr>

#### 4. Define a function ```return-as-is``` that takes a single argument x and returns it without any change.

Answer:
```Clojure
user=> (defn return-as-is [x] x)  ;; be careful, it is NOT (x), namely, not further evaluation
#'user/return-as-is

user=> (return-as-is 123)
123

user=> (source identity)
(defn identity
  "Returns its argument."
  {:added "1.0"
   :static true}
  [x] x)
nil
```

<hr>

#### 5. Define a function ```just-1000``` which takes any number of arguments, ignores all of them, and returns the number 1000.

Answer:
```Clojure
user=> (defn just-1000 [& any_args] 1000)
#'user/just-1000

user=> (just-1000 1 10 100 1000 10000)
1000
```

<hr>

#### 6. Define a function ```just-one-arg``` which takes a single argument x. It should return another function, which takes any number of arguments and always returns x.

Answer:
```Clojure
user=> (defn just-one-arg [x]
  (fn [& any_args] x))
#'user/just-one-arg
  
user=> ( (just-one-arg 123) 456 789 'abc' )
123

user=> (source constantly)
(defn constantly
  "Returns a function that takes any number of arguments and returns x."
  {:added "1.0"
   :static true}
  [x] (fn [& args] x))
nil
```

<hr>

#### 7. Define a function ```five_times``` which takes another function and calls it 5 times, without any arguments.

Answer:
```Clojure
(defn five_times [another_func] (another_func) (another_func) (another_func) (another_func) (another_func))
```

<hr>

#### 8. Define a function ```negation``` which takes a single argument ```func```. It should return another function which takes any number of arguments, applies ```func``` on them, and then calls ```not``` on the result. The ```not``` function in Clojure does logical negation.

Answer:
```Clojure
(defn negation [func]
  (fn [& any_args] (not (apply func args))))
```

This is the ```complement``` function in Clojure:

```Clojure
(defn complement
  "Takes a function f and returns a function that takes the same arguments as f,
  has the same effects, if any, and returns the opposite truth value."
  [f]
  (fn
    ([] (not (f)))
    ([x] (not (f x)))
    ([x y] (not (f x y)))
    ([x y & zs] (not (apply f x y zs)))))
```

<hr>

#### 9. Define a function ```five_times_plus``` which takes another function and any number of arguments, then calls that function 5 times on those arguments. Re-use the function you defined in the earlier ```five_times``` exercise.

Answer:
```Clojure
(defn five_times_plus [f & any_args]
  (five_times (fn [] (apply f any_args))))
```

<hr>

#### 10. Using the <a href="https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html">java.lang.Math</a> class (Math/pow, Math/cos, Math/sin, Math/PI), demonstrate the following mathematical facts:
- The cosine of pi is -1
- For some x, sin(x)^2 + cos(x)^2 = 1

Answer:
```Clojure
user=> (Math/cos Math/PI)
-1.0

user=> (def x 0.3)
#'user/x

user=> (+ (Math/pow (Math/sin x) 2) (Math/pow (Math/cos x) 2))
1.0
```

<hr>

#### 11. Define a function that takes an HTTP URL as a string, fetches that URL from the web, and returns the content as a string.

Hint: Using the <a href="https://docs.oracle.com/javase/8/docs/api/java/net/URL.html">java.net.URL</a> class and its ```openStream``` method. Then use the Clojure <a href="https://clojuredocs.org/clojure.core/slurp">```slurp```</a> function to get the content as a string.

Answer:
```Clojure
user=> (defn http-get [HTTP-URL]
  (slurp
    (.openStream
      (java.net.URL. HTTP-URL))))
#'user/http-get

user=> (assert (.contains (http-get "https://clojure.org") "Clojure"))     
nil
```

As the Clojure <a href="https://clojuredocs.org/clojure.core/slurp">```slurp```</a> function interprets its argument as a URL first before trying it as a file name. Write a simplified http-get:

Answer:
```Clojure
user=> (defn http-get [HTTP-URL]
  (slurp HTTP-URL))
#'user/http-get

user=> (assert (.contains (http-get "https://clojure.org") "Clojure"))
nil
```

<hr>

#### 12. Define a function ```more-args``` that takes two arguments:

- f, a function
- x, a value

and returns another function which calls f on x plus any additional arguments.

Answer:
```Clojure
user=> (defn more-args [f x]
  (fn [& any_args] (apply f x any_args)))
#'user/more-args
  
user=> (source partial)
(defn partial
  "Takes a function f and fewer than the normal arguments to f, and
  returns a fn that takes a variable number of additional args. When
  called, the returned function calls f with args + additional args."
  {:added "1.0"
   :static true}
  ([f] f)
  ([f arg1]
   (fn
     ([] (f arg1))
     ([x] (f arg1 x))
     ([x y] (f arg1 x y))
     ([x y z] (f arg1 x y z))
     ([x y z & args] (apply f arg1 x y z args))))
  ([f arg1 arg2]
   (fn
     ([] (f arg1 arg2))
     ([x] (f arg1 arg2 x))
     ([x y] (f arg1 arg2 x y))
     ([x y z] (f arg1 arg2 x y z))
     ([x y z & args] (apply f arg1 arg2 x y z args))))
  ([f arg1 arg2 arg3]
   (fn
     ([] (f arg1 arg2 arg3))
     ([x] (f arg1 arg2 arg3 x))
     ([x y] (f arg1 arg2 arg3 x y))
     ([x y z] (f arg1 arg2 arg3 x y z))
     ([x y z & args] (apply f arg1 arg2 arg3 x y z args))))
  ([f arg1 arg2 arg3 & more]
   (fn [& args] (apply f arg1 arg2 arg3 (concat more args)))))
nil
```

<hr>

#### 13. Define a function ```f-and-g``` which takes two functions as arguments, f and g. It returns another function which takes one argument, x, calls g on it, then calls f on the result, and returns that.

Answer:
```Clojure
user=> (defn f-and-g [f g]
  (fn [x] (f (g x))))
#'user/f-and-g
```
