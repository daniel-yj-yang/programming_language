
# <a href="./README.md">Clojure</a> (<a href="https://clojure.org/api/cheatsheet">Cheat Sheet</a>)

## <a href="./Syntax.md">Syntax</a>

### Evaluation

<hr>

#### 1. Clojure Evaluation

- The **Reader** reads a series of Clojure expression and produces Clojure data.
- The **Reader** is separate from the **Compiler**, making room for macros, which take data and emit data.

<hr>

#### 2. Clojure Structure and Semantics

```Clojure
(+ 5. 8.)
```

--- | --- | () | ```+``` | 5. and 8.
--- | --- | --- | --- | ---
The Reader understands | this example Clojure expression as | list | symbol | numbers (floats)
The Compiler interprets ... | this example Clojure semantics as | invocation | function | arguments
