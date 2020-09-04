- <a href="http://incanter.org/docs/incanter-cheat-sheet.pdf">cheat sheet</a> (<a href="./incanter/incanter-cheat-sheet.pdf">local save</a>)
- http://incanter.github.io/incanter/index.html
- https://github.com/incanter/incanter/wiki

### Examples:

#### Normal distribution PDF

##### 1. using <a href="https://incanter.github.io/incanter/stats-api.html">sample-normal</a>

```Clojure
user=> (view (histogram (sample-normal 10000000 :mean 0 :sd 1) :nbins 1000 :density true :x-label "Normal Distribution PDF"))
```
<img src="./images/normal_distribution_pdf_1.png">

<hr>

##### 2. using <a href="https://incanter.github.io/incanter/stats-api.html">pdf-normal</a>

```Clojure
user=> (view (function-plot pdf-normal -5 5))
```
<img src="./images/normal_distribution_pdf_2.png">

<hr>

References of incanter <a href="https://incanter.github.io/incanter/stats-api.html">functions</a>

<a href="https://github.com/incanter/incanter/wiki/Probability-Distributions">CDF</a> | <a href="https://github.com/incanter/incanter/wiki/Probability-Distributions">PDF</a> | <a href="https://github.com/incanter/incanter/wiki/Probability-Distributions">sample</a> | distance 
--- | --- | --- | ---
cdf-beta<br/>cdf-binomial<br/>cdf-chisq<br/>cdf-empirical<br/>cdf-exp<br/>cdf-f<br/>cdf-gamma<br/>cdf-neg-binomial<br/>cdf-normal<br/>cdf-poisson<br/>cdf-t<br/>cdf-uniform<br/>cdf-weibull | pdf-beta<br/>pdf-binomial<br/>pdf-chisq<br/>pdf-exp<br/>pdf-f<br/>pdf-gamma<br/>pdf-neg-binomial<br/>pdf-normal<br/>pdf-poisson<br/>pdf-t<br/>pdf-uniform<br/>pdf-weibull | sample<br/>sample-beta<br/>sample-binomial<br/>sample-chisq<br/>sample-dirichlet<br/>sample-exp<br/>sample-gamma<br/>sample-inv-wishart<br/>sample-multinomial<br/>sample-mvn<br/>sample-neg-binomial<br/>sample-normal<br/>sample-permutations<br/>sample-poisson<br/>sample-t<br/>sample-uniform<br/>sample-weibull<br/>sample-wishart | chebyshev-distance<br/>euclidean-distance<br/>hamming-distance<br/>jaccard-distance<br/>lee-distance<br/>levenshtein-distance<br/>mahalanobis-distance<br/>manhattan-distance<br/>minkowski-distance<br/>normalized-kendall-tau-distance

<hr>

#### Hyperbolic tangent PDF

```Clojure
user=> (defn tanh [x] (/ (- (exp x) (exp (* -1 x))) (+ (exp x) (exp (* -1 x)))))
#'user/tanh

user=> (view (function-plot tanh -5 5))
```

<img src="./images/tanh_1.png">
