# Lists

### Basics
```
Nil = List[Nothing] <: List[T]
```
By this covariant property, we don't have to make seperate `Nil` for every type.

### Tuples
- Generalizes `pair`
- Also supports pattern matching for each item ; uses case class internally
- It reduces memory by optimizing primitive types not to generate seperate object for each entry.
```scala
case casee Tuple2[
  @specialized(Int, Long, Double, ...., AnyRef) + T1,
  @specialized(Int, Long, Double, ...., AnyRef) + T2
]
```

### Implicit
```
def sum[A] (xs: List[A])(implicit m : Monoid[A]) : A = 
  ...
  
println( sum(List(1,2,3) ) # No 2nd argument?
```
Whenever the parameter is missing and it is missing, it searches for implicit context in the code and automatically applies it.  
Do not use frequently, especially when it is hard to follow the design concept.

### Higher-Order List Functions
- map
- filter
- partition
- reduceLeft
- foldLeft

### Collections
- List
- Seq
- Map
- HashMap
- Vector (is very powerful in scala!, prefer using `Vector` to `Array`)
- Array
