
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

## <a href="./Functions.md">Functions</a>

### Java Interop

<hr>

#### 1. Invoking Java code

Calling into Java from Clojure

Task | Clojure | More Clojure Examples
--- | --- | ---
Instantiation | (Widget. "foo") | (<a href="https://docs.oracle.com/javase/7/docs/api/java/net/URL.html">java.net.URL.</a> HTTP-URL)
Instance method | (.nextInt rnd) | (<a href="https://docs.oracle.com/javase/8/docs/api/java/net/URL.html">.openStream</a> x)
Instance field | (.-field object) | ---
Static method | (Math/sqrt 36) | (<a href="https://docs.oracle.com/javase/7/docs/api/java/lang/Math.html">Math/tanh</a> Math/PI)
Static field | Math/PI | <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/Math.html">Math/E</a>

<hr>

#### 2. Java Methods vs Functions

Java methods (e.g., .length) can be wrapped in Clojure functions when necessary

```Clojure
user=> ( #(.length %) "abc" )
3
```
