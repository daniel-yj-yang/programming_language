<a href="https://github.com/mikera/core.matrix/wiki">core.matrix</a>

### Examples:

```Clojure
user=> (require '[clojure.core.matrix :as ccm])
nil

user=> (require '[clojure.core.matrix.linear :as ccml])
nil

user=> (def A (ccm/matrix [[1.5 0.5] [0.5 1.5]]))
#'user/A

user=> A
[[1.5 0.5] [0.5 1.5]]

user=> (type A)
clojure.lang.PersistentVector

user=> (ccml/svd A) ;; see https://github.com/mikera/core.matrix/issues/338
Execution error (ExceptionInfo) at clojure.core.matrix.impl.defaults/eval11871$fn (defaults.cljc:2623).
TODO: Not yet implemented: (mp/svd m options) for class clojure.lang.PersistentVector

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; Approach 1 - use :vectorz (recommended)
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

user=> (def A (ccm/matrix :vectorz [[1.5 0.5] [0.5 1.5]]))
#'user/A

user=> A
#vectorz/matrix [[1.5,0.5],
[0.5,1.5]]

user=> (type A)
mikera.matrixx.Matrix
```

user=> (ccml/svd A)
{:U #vectorz/matrix [[0.7071067811865474,0.7071067811865474],
[0.7071067811865474,-0.7071067811865474]], :S #vectorz/vector [1.999999999999999,0.9999999999999996], :V* #vectorz/matrix [[0.7071067811865474,0.7071067811865475],
[0.7071067811865475,-0.7071067811865474]]}

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; Approach 2 - use set-current-implementation
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

user=> (ccm/set-current-implementation :vectorz)
:vectorz

user=> (def A (ccm/matrix [[1.5 0.5] [0.5 1.5]]))
#'user/A

user=> A
#vectorz/matrix [[1.5,0.5],
[0.5,1.5]]

user=> (type A)
mikera.matrixx.Matrix

