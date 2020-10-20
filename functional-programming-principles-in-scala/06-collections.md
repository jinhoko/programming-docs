# Collections

### Collection Hierarchy
![img](https://docs.scala-lang.org/resources/images/tour/collections-immutable-diagram.svg)
Bold lines are the base data structure for nonleaf nodes!

### Partial Functions
```
val f = { 
  case cond1 => v1
  case cond2 => v2
}
f : PartialFunction 
```
f returns a function. Syntactic sugar.

### for comprehension
```
for {
  i <- 1 until n  => generator
  j <- 1 until i  => generator
} yield (i, j)
```
It simply retranslates to resolved scala code. Also a syntactic sugar!  
Monad programming. *(what is monad programming?)*

### map, flatten, flatMap
`xs flatMap f = (xs map f).flatten`

### Translating `for comprehension`
`(1 until n).flatMap i => (1 until i).flatMap j => content`  
Which statement to use? : It is much better to implicitly handle loops just by using `while loop`.


