Clojure is a dialect for Lisp. It is a hosted langauge. Clojure programs are translated to Java Bytecode and then executed
by JVM. Clojure relies on JVM for features such as threading and garbage collection.



```
user=> (str "Carnegie" "Mellon")
"CarnegieMellon"
```

Clojure 'statements' or expressions are also called as forms.
```
user=> [1 2 3]
[1 2 3]
```
```
user=> 1
1
```
```
user=> "random string"
"random string"
```
```
user=> ["string" "vector"]
["string" "vector"]
```

Conditionals
```
user=> (if true
  #_=>     "this is true"
  #_=>     "this is false"
  #_=> )
"this is true"
```
```
user=> (if false
  #_=>     "this is true"
  #_=>     "this is false"
  #_=> )
"this is false"
```

```
user=> (if false
  #_=>     "blah"
  #_=> )
nil
```
In Clojure, each branch of the if statement can have only one form. So to have multiple forms in a conditional branch, we use 
the do statement.

### Boolean Expressions
`and` returns the first falsey of the last truthy value. 'or' returns the first truthy or last falsey value.

`nil?` function checks if a value is nil.

```
user=> (nil? nil)
true
user=> (nil? 1)
false
```

You can do direct string comparison in Clojure.
```
user=> (= "ha" "ha")
true
user=> (= 4 3)
false
```

Define a hashmap and get values:
```
user=> (def alex {:a 1 :b 2})
#'user/alex

user=> (get alex :a)
1
user=> (get alex :b)
2
user=> (alex :b)
2
user=> (get alex :n)
nil
```
Nested maps:
```
user=> (def alex {:a 1 :b "alia" :c {:a 9 :b 8}})
#'user/alex
user=> (get alex :c)
{:a 9, :b 8}
user=> (get (get alex :c) :a)
9
user=> (get-in alex [:c :b])
8
```
Get function default return value
```
user=> (get alex :x "nooooo!")
"nooooo!"
```
Keywords are used primarily as keys in maps. They can also be used to as a replacement for the get function.
```
user=> (def alex {:a 1 :b 2})
#'user/alex
user=> (:a alex)
1
```

Vectors
These are zero-indexed collections.
```
user=> (def v [1 2 3])
#'user/v
user=> (get v 1)
2
user=> (get v 0)
1
user=> (vector "this" "is" "sparta")
["this" "is" "sparta"]
user=> (conj v 4)
[1 2 3 4]
```
Lists are also a linear collection of values. You cannot use `get` to fetch values. You have ot use the `nth` function.
```
user=> (def l (list 1 2 "3"))
#'user/l
user=> (nth l 0)
1
user=> (nth l 2)
"3"
user=> (nth l 3)

IndexOutOfBoundsException   clojure.lang.RT.nthFrom (RT.java:885)
```
```
user=> (def l `(1 2 3))
#'user/l
user=> (nth l 2)
3
```
Sets are like sets in other languages, store unique elements.
```
user=> (def s #{1 2 3})
#'user/s
user=> (conj s 4)
#{1 4 3 2}
user=> (contains? s 2)
true
user=> (contains? s 5)
false
```
### Functions
Increment
```
boot.user=> (inc 3)
4
```
Parameters
```
(defn no-params
  []
  "I take no parameters!")
(defn one-param
  [x]
  (str "I take one parameter: " x))
(defn two-params
  [x y]
  (str "Two parameters! That's nothing! Pah! I will smoosh them "
  "together to spite you! " x y))
```
Rest parameter. Similar to varargs in C. The rest of the parameters come in as a list.
```
boot.user=> (defn crew
       #_=>   [name & rest]
       #_=>   (str "Hi, " name "! Your crew has: " rest)
       #_=>   )
#'boot.user/crew
boot.user=> (crew "alex" "balia" "naiya" "joya")
"Hi, alex! Your crew has: (\"balia\" \"naiya\" \"joya\")"
```




### FILE I/O
```
(use 'clojure.java.io)
(with-open [wrtr (writer "/tmp/test.txt")]
  (.write wrtr "Line to be written"))
```
```
(slurp "/tmp/test.txt")
```
```
(use 'clojure.java.io)
(with-open [rdr (reader "/tmp/test.txt")]
  (doseq [line (line-seq rdr)]
    (println line)))
```

### MISC
```
boot.user=> (clojure.string/join "," ["this" "is" "comma" "separated"])
"this,is,comma,separated"
```
