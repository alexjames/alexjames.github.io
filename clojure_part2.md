### Accessing elements of a collection
```
user=> (def data [1 2 3 4 5])
#'user/data
user=> (first data)
1
user=> (rest data)
(2 3 4 5)
user=> (last data)
5
```
### Fun with maps
```
user=> (map str ["a" "B" "c"] ["1" "2" "3"])
("a1" "B2" "c3")

user=> (map :score [{:game "1" :score 33} {:game "2" :score 54} {:something-else 9}])
(33 54 nil)

```
