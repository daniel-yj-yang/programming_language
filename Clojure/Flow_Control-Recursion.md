# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

## <a href="./Sequential_Collections.md">Sequential Collections</a>

## <a href="./Hashed_Collections.md">Hashed Collections</a>

## <a href="./Flow_Control.md">Flow Control</a>

### Recursion

<hr>

#### 1. Recursion and Iteration

- Clojure provides recur and the sequence abstraction
- <a href="https://clojure.org/reference/special_forms#recur">```recur```</a> is "classic" recursion, but consumers don’t control it, considered a lower-level facility
- Sequences represent iteration as values, and onsumers can partially iterate
- Reducers represent iteration as function composition

<hr>

#### 2. ```loop``` and ```recur```

- Functional looping construct: ```loop``` defines bindings, while ```recur``` re-executes loop with new bindings
- Prefer higher-order library functions instead

Example:
```Clojure
user=> (defn Example []
   (loop [x 10]               ;; first binding the value of 'x' to 10 using the loop statement
      (when (> x 1)           ;; then using the when condition clause to see if the value of 'x' > 1. If x is not > 1, stop the loop
         (println x)          ;; then printing the value of 'x' to the console
         (recur (- x 2)))))   ;; finally using the recur statement to repeat the loop, after the value of 'x' is decremented by 2
#'user/Example

user=> (Example)
10
8
6
4
2
nil
```

Example:
```Clojure
user=> (loop [i 0]              ;; first binding the value of 'i' to 0 using the loop statement
  (if (< i 10)                  ;; then using the if condition clause to see if the value of 'i' < 10, 
    (do
      (println (str "i = ", i)) ;; return a string
      (recur (inc i)))          ;; then using the recur statement to repeat the loop, after the value of 'i' is incremented by 1
    "i = 10"))                  ;; if i is not < 10, return a string and stops the loop
i = 0
i = 1
i = 2
i = 3
i = 4
i = 5
i = 6
i = 7
i = 8
i = 9
"i = 10"
```

<hr>

#### 3. ```defn``` and ```recur```

- Function arguments are implicit ```loop``` bindings

Example:
```Clojure
user=> (defn increase [i]
  (if (< i 10)
    (recur (inc i))
    i))
#'user/increase

user=> (increase 5)
10
```

<a href="https://forum.freecodecamp.org/t/clojure-guide-how-to-use-loop-and-recur/18418">Example</a>:
```Clojure
user=> (defn fact [x]
  (loop [n x, product 1]                ;; binding n to x, and binding prod to 1.
    (if (= 1 n)                         ;; this is the base case, the condition to make the loop stop looping, here it says if n = 1, loop stops and returns product
      product
      (recur (dec n) (* product n)))))  ;; if n is not 1, the loop recurs. recur restarts the loop with different bindings: n = n - 1, and product = product * n
#'user/fact

user=> (fact 10)
3628800
```

<hr>

#### 4. ```recur``` for recursion

- <a href="https://clojuredocs.org/clojure.core/recur">```recur```</a> must be in "tail position", that is, the last expression in a branch
- ```recur``` must provide values for all bound symbols by position, including: (a) loop bindings, and (b) defn/fn arguments
- Recursion via ```recur``` does not consume stack
