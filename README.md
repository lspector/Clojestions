### Clojestions: Suggested exercises for learning Clojure
Lee Spector (lspector@hampshire.edu), 2018


---

### Numeric expressions

Write and evaluate expressions that combine numbers, like `(+ 1 2)` and `(* 1.23 2).` 

Try all of the functions in the "Arithmetic" section of the [Clojure cheat sheet](https://clojure.org/api/cheatsheet). 

Try nested expressions that use several functions, like `(+ 1 (* 2 3))`. 

Try doing things with ratios like `1/3`, and functions that can take any number of arguments, like `+`, which you can use like `(+ 1 2 3 4 5)`. 

Try using enormous numbers and tiny numbers, and seeing what produces errors and what doesn't.

Write and evaluate an expression that calculates the number of seconds in a year.


---

### Random numeric expressions

Write and evaluate expressions that use `rand-int`, which returns random integers, and `rand`, which returns random floating-point numbers. 

Try combining these with arithmetic functions in complex expressions.

---

### Expressions with local variables

 Write and evaluate expressions that use `let` to bind symbols to numbers, and then combine those numbers using arithmetic functions, like:

```
(let [x 2
      happiness 3]
  (+ (* x x) happiness))
```

Experiment with expressions that bind the same symbol many times, like:

```
(let [x 0
      x (+ x 1)
      x (* x 100)
      x (/ x 20)]
  x)
```

Write and evaluate an expression that uses `let` to bind `diameter` to some value and then returns the area of a circle with that diameter.

Write and evaluate arithmetic expressions for other formulas that you remember (or look some up if you don't remember any).

---

### Threading

Write and evaluate expressions that use the "threading" macros `->` and `->>` to express arithmetic expressions in sequental order, like:

```
(-> 95
    (+ 5)
    (* 2)
    (- 1))
```
which is an alternative syntax for `(- (* (+ 95 5) 2) 1)`.

Evaluate the same expressions with `->>` substituted for `->` and vice versa, and compare the results.

Threading can be used with any data types, not just numbers, so when you are familiar with other types, try rewriting nested expressions that involve them using threading.

---

### Logical/Boolean expresions

Write and evaluate expressions that combine `true` and `false` (which are also called "Boolean" values) using `and`, `or`, and `not`, like `(and true (not false))`. 

---

### Arithmetic comparisons and tests

Write and evaluate expressions that use the arithmetic comparison functions `==`, `<`, `>`, `<=`, `>=`, which take numbers and return Boolean values.

Write and evaluate expressions that use numerical test functions such as `zero?`, `pos?`, `neg?`, `even?`, and `odd?`.

---

### Conditional numeric expressions

Write and evaluate expressions that use `let` to bind symbols to numbers (maybe from expressions that return numbers) and then `if` to return different things depending on comparisons among the numbers (maybe involving Boolean combinations as well), like:

```
(let [choice (rand-int 100)]
  (if (and (> choice 42)
           (not (odd? choice)))
    (/ choice 2)
    choice))
```

Write and evaluate expressions that use `cond` and `case` rather than `if`.

---

### Vectors of numbers

Write and evaluate expressions that combine vectors of numbers (like `[1 2 3]` and `[99 -1.23 0 123454321]`) with functions like `concat`, `rest`, `distinct`, `flatten`, `reverse`, `shuffle`, and `interleave`. 

Write and evaluate nested expressions using these functions and vectors, like:

```
(concat (distinct [1 2 3 2 1 2 1])
        (shuffle (rest [100 200 300 400]))
        (interleave [11 11 11 11] [22 22 22 22]))
```

Some of these functions actually return "lazy sequences" rather than vectors. They are called "lazy" because their elements aren't all computed until they are needed (more on this later), and they are printed with `()` parentheses, looking like lists. Write and evaluate expressions using the `type` function to see what types are returned from various expressions (you'll see the names of underlying Java types). Write and evaluate expressions using `vec` to convert the results of various expressions to vectors.

Use `let` to bind symbols to your vectors, which can make the expressions easier to read. 

Try incorporating functions that also take integer arguments like `take`, `drop`, and `partition`, like:

```
(let [v [1 2 3 4 5 6 7 8 9 10]]
  (partition 2 (take 6 (drop 1 v))))
```

Try adding new numbers to vectors with `conj`. 

Try changing elements of vectors with `assoc`, like `(assoc [10 10 10] 1 99)`.

Try adding new vectors to vectors, building nested vectors, like:

```
(conj [[1 2][3 4]]
      [5 6])
```

Use `first`, `second`, `last`, `nth`, and `rand-nth` to return specific items from within (possibly nested) vectors.

Write and evaluate expressions using `count` to get the number of items in a vector, and `=` to compare vectors.

Write an evaluate expressions using `range` to generate sequences of numbers, and then convert them to vectors of numbers. 

---

### Lists of symbols

Write and evaluate expressions that combine lists of symbols (like `'(a b c) `and `'(hello world)`) with functions like `concat`, `rest`, `distinct`, `flatten`, `reverse`, `shuffle`, and `interleave`. 

Write and evaluate deeply nested expressions using these functions and lists of symbols.

Use `let` to bind symbols to your lists, which can make the expressions easier to read. 

Try incorporating functions that also take integer arguments like `take`, `drop`, and `partition`. 

Try adding new symbols to lists with `conj`, like `(conj '(walk the) 'dog)`, and notice how this acts differently on lists than on vectors. Also try adding new symbols to lists with `cons`.

Try adding new lists to lists with `conj` and `cons`, building nested lists.

Write and evaluate expressions that build complicated nested lists using only `cons`, quoted symbols, and `()`.

Write and evaluate expressions that pull various parts out of nested lists using nested calls to `nth`, like:

```
(nth (nth (nth '((it was) a nested ((list of (lists and symbols)))
                 that did not amount to much) 
               3) 
          0) 
     2)
```

Use `first`, `second`, `last`, `nth`, and `rand-nth` to return specific/random items from within (possibly nested) lists.

Write and evaluate expressions using `count` to get the number of items in a list, and `=` to compare lists.

---

### Vectors of keywords

Write and evaluate expressions that manipulate vectors of keywords, which are just symbols that start with ":", like `:eggplant` and `:duck`. Note that unlike other symbols, keywords evaluate to themselves, so they don't have to be quoted and you can write something like `[:alpha :beta :petunia]` to get a vector of three symbols, whereas to do the same thing without keywords you'd either have to quote the whole thing like `'[alpha beta petunia]` or quote each element like `['alpha 'beta 'petunia]`.

---

### Functions that evaluate

Write and evaluate expressions that return lists containing numbers and symbols that name arithmetic functions (like `+`), in orders that constitute valid arithmetic expressions, and wrap these expressions in calls to `eval`, like `(eval (concat '(+ 1) '(2 3)))`.

Write and evaluate functions that build lists of numbers and then use `apply` to call functions with all of the items as arguments, like `(apply + (concat '(1 2 3) '(4 5)))`.

---

### Mapping functions down vectors of numbers

Write and evaluate expressions that use `mapv` to call a 1-argument function oone each item in a vector of numbers and return a vector of the results, like `(mapv inc [1 2 3])` and `(mapv odd? [1 2 3])`. 

You can use `map` instead of `mapv`, but that will return a lazy sequence (which looks like a list when it is printed) rather than a vector.

Write and evaluate expressions that use `mapv` or `map` to call multi-argument functions on multiple vectors, like `(map * [1 2 3] [4 5 6])`.


---

### Filtering sequences of numbers

Write and evaluate expressions that use `filter` and numerical test functions such as `zero?`, `pos?`, `neg?`, `even?`, and `odd?` to filter vectors or lists or lazy sequences of numbers, like `(filter even? (range 10 20))`.

---

### Numeric function definitions

Write and evaluate expressions that define functions that take and return numbers, like:

```
(defn add3 [n]
  "Returns n plus 3."
  (+ n 3))
```

and

```
(defn sum-squares [x y]
  "Returns x squared plus y squared."
  (+ (* x x)
     (* y y)))
```

Write functions that compute geometric formulae, like a `circle-area` function that takes a `diameter` argument and returns the area of a circle with the given area.

Then write and evaluate expressions (including nested expressions) that call these functions, like:

```
(let [perfect 3
      answer 42]
  (+ (add3 perfect)
     (sum-squares (add3 answer)
                  (add3 perfect))))
```

Write and evaluate expressions that use `map` and `filter` with the numeric functions that you have defined, operating on lists or vectors of numbers, like `(map add3 [1 2 3])`.

---

### Anonymous functions

Write and evaluate expressions using `map` and `filter` with numeric functions operating on lists or vectors of numbers, but instead of defining the functions with `defn`, include their definitions directly (anonymously) in the `map` and `filter` expressions, like:

```
(map (fn [n] (+ n 3))
     [1 2 3])
```

and

```
(filter (fn [n] (> n 3))
        (range 10))
```

Then re-write some of your expressions to use the "shorthand" anonymous function syntax, like:

```
(map #(+ % 3)
     [1 2 3])
```

and

```
(filter #(> % 3)
        (range 10))
```

---

### Sequences of sequences

Write and evaluate expressions using `map` and `filter` on vectors and lists *that contain* vectors and lists, like:

```
(map #(apply max %)
     [[1 2 3][93 37 493 23][-2 1/2 0.0]])
```

---

### Random text and music

Write functions that return randomly-chosen words of a particular grammatical category as symbols, like:

```
(defn random-noun []
  "Returns a random noun."
  (rand-nth '(beachball turnip alligator book globe)))
```

Write functions using these functions that return random phrases and sentences as lists of symbols. Then write and evaluate expressions using these functions.

Write and call a function that returns a haiku as a list of three lists of symbols, one for each line of the haiku.

Write and call a function that returns song lyrics that include repeated lines and sections.

Write and call a function that returns nested lists and vectors representing music, in the proper syntax for the [Klangmeister website](https://ctford.github.io/klangmeister/). Then paste the results of your calls into the website and listen to them.

---

### Infinite lazy sequences

Write and evaluate expressions that use `repeat` with just one argument, to create infinite lazy sequences of that argument, but **always** wrap these expressions in other calls that return only finite sub-sequences and ***be careful not to return, and therefore to try to print, the full infinite sequence***. For example, `(repeat 1)` will return an infinite sequnece of 1s, and typing that into a REPL will do something **bad**. But `(take 23 (repeat 1))` is fine, and will return a sequence of 23 1s.

Write and evaluate expressions that use `repeat` with two arguments, the first of which should be the number of repetitions.

Write and evaluate expressions that use `repeatedly`, like `(take 10 (repeatedly rand))`, again being careful not to try to print an infinite sequence.

Write and evaluate expressions that use `iterate`, like `(take 10 (iterate #(+ % 10) 0))`, gain being careful not to try to print an infinite sequence.

---

### Strings

Write and evaluate expressions that combine strings of characters (like `"this is a string"` and `"I love you!"`) with `str`, like `(str "Hello" " world!")`.

Write and evaluate expressions that combine strings of characters with sequence functions like `concat`, `rest`, `distinct`, `reverse`, and `interleave`.  Note that you can turn a lazy sequence of characters, which is what these functions will return, back into a string with `apply` and `str`, like `(apply str (map #(char (inc (int %))) "abc"))`.

---

### Sequence comprehensions with `for`

Write and evaluate expressions that use `for` with multiple sequences to process all combinations of elements from the sequences, like:

```
(for [thing ["fish" "wish" "dish"]
      number [1 2 3 4]]
  (if (= number 1)
    (str number " " thing)
    (str number " " thing "es")))
```

or:

```
(for [i [1 2 3]
      j [10 100 100]]
  (* i j))
```

---

### Input and output

Write and evaluate expressions using `println`, noting that this has the side effect of printing but always just returns nil.

Write and evaluate expressions that write text to files with `spit` and that read strings from files with `slurp`.

Write and evaluate expressions that read Clojure expressions from strings using `read-string`, and then evaluate or manipulate the resulting Clojure data, like `(eval (read-string (str "(+ 1" " 2)")))`.

---

### `loop` and `recur`

Write and evaluate expressions that use `loop`, with one or more loop variables, and `recur` to return to the top of the loop with new values for the variables. Be sure to test for the exit condition within the loop, and not to `recur` when the condition is met, like:

```
(loop [x 0]
  (if (> (* x x) 100)
    x
    (recur (inc x))))
```

which returns the lowest integer that has a square greater than 100.

---

### Factorials

Write and call a function that returns the factorial of a positive integer *n*, which is *n* times *n-1* times *n-2* times ... 1. For example, the factorial of 5 is 120.

Try writing this with `loop` and `recur`, or alternatively with `map` or in other ways. Several implementations are given in [clojinc](https://github.com/lspector/clojinc).

---

### Sets of numbers

Write and evaluate expressions that combine sets of numbers (like `#{1 2 3}` and `{1 3 7}`) with functions like `clojure.set/intersection`, `clojure.set/union`, and `clojure.set/difference`. If you evaluate `(use clojure.set)` then afterwards you can use `intersection`, `union`, and `difference` without the `clojure.set/` prefix.

Use `some` to test whether something occurs in a set, like `(some #{3} #{1 2 3 4 5})`. 

---

### Hash maps

Write and evaluate expressions that use hash maps to represent structured data, like:

```
{:name {:first "Edgar", :middle "Allen", :last "Poe"}, 
 :born 1809, 
 :birthplace {:city "Boston", :state "MA"}, 
 :residence {:city "Baltimore", :state "MD"}}
```

Write and evaluate expressions that pull out parts of the data, like `(:city (:birthplace p))` where `p` is bound to a map like the one above.

Write and evaluate expressions that use `assoc` and `dissoc` to return altered versions of your maps.

---

### Java interop

Write and evaluate expressions that combine numbers using not just Clojure functions, but also Java library functions like `Math/sqrt` and `Math/log`, the Java constant `Math/PI`, and other functions and constants described in the [Java documentation](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html).

---

### A lot more

Write and evaluate variants of the expressions in [clojinc](https://github.com/lspector/clojinc), and complete the exercises therein.
