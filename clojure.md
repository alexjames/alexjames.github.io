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

### Conditionals
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

```
boot.user=> (if true
       #_=>   (do (println "yeah")
       #_=>       (println "this is nice")
       #_=>       1)
       #_=> )
yeah
this is nice
1
```
`when` combines the two if you don't have an else statement:
```
boot.user=> (when true
       #_=>   (println "Yeah!")
       #_=>   "Booyeah!")
Yeah!
"Booyeah!"
```

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

### Collections
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
Clojure always returns the last form from a function's body.
```
#'boot.user/fn
boot.user=> (defn newfn
       #_=>   []
       #_=>   (+ 2 3)
       #_=>   "yeah!"
       #_=>   ["hola" "cena"])
#'boot.user/newfn
boot.user=> (newfn)
["hola" "cena"]
```
Anonymous function have no name.
```
boot.user=> #(* % 3)
3#object[boot.user$eval2105$fn__2106 0x6c94a7f5 "boot.user$eval2105$fn__2106@6c94a7f5"]
boot.user=> (map #(* % 3) '(1 2 3))
(3 6 9)
```
```
boot.user=> (#(str %1 " and " %2) "batman" "robin")
"batman and robin"
```
`map` applies a function to all members of a collection
```
boot.user=> (map inc [1 2 3 4])
(2 3 4 5)
boot.user=> (map #(* 3 %) [1 2 3 4])
(3 6 9 12)
boot.user=> (map odd? [1 2 3 4])
(true false true false)
```
Map destructuring
```
boot.user=> (defn break-map 
       #_=>   [{n :name a :age}]
       #_=>   (println (str "My name is " n)))
#'boot.user/break-map
boot.user=> (break-map {:name "alex" :age 20})
My name is alex
nil
boot.user=> (break-map {:age 20})
My name is 
nil
```
Returning functions
```
boot.user=> (defn inc-maker
       #_=>   "Create a custom incrementor"
       #_=>   [inc-by]
       #_=>   #(+ % inc-by))
#'boot.user/inc-maker

^^^
This function returns a function. The inner "returned" function will add the first argument (%) passed to it
by inc-by. The value of inc-by is provided through the call to the "outer" function.

boot.user=> (map (inc-maker 3) [1 2 3])
(4 5 6)
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
Join function
```
boot.user=> (clojure.string/join "," ["this" "is" "comma" "separated"])
"this,is,comma,separated"
```

Type of a data structure
```
boot.user=> (type pok-data)
clojure.lang.PersistentArrayMap
```
