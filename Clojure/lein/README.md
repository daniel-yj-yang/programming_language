lein: https://leiningen.org/

<hr>

Usage:

1. "<a href="https://cljdoc.org/d/leiningen/leiningen/2.9.4/api/leiningen.new">new</a>" - Generate project scaffolding based on a <a href="https://clj-templates.com/">template</a>.

Using the template "app" to create project "clojure-app"
```
lein new app clojure-app
```

<hr>

2. "<a href="https://cljdoc.org/d/leiningen/leiningen/2.9.4/api/leiningen.deps">deps</a>" - Download and examine dependencies

By default, lein stores downloaded dependencies in the default path ~/.m2/repository/

As described <a href="https://github.com/technomancy/leiningen/blob/master/sample.project.clj">here</a>, this default path can be changed by putting a profiles.clj in ~/.lein

```Clojure
{:user  {;Location of local repository 
         :local-repo "Drive/Path"
         ;Location of locally installed jars
         ;(that can't be downloaded from public repo's)
         :repositories  {"local" {:url "file://Drive/Path"
                                  :releases {:checksum :ignore}}}}}
```
