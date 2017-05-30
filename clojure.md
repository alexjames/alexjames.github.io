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
```
Get function default return value
```
user=> (get alex :x "nooooo!")
"nooooo!"
```

