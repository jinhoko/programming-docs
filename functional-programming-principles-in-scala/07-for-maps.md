# For, Maps

### Mini-Database
```
val books: List[Book] = List(
  Book(title= "", author=List("","","",),
  Book(),...
)
```

### Query
SQL style for-loop
```
val bookset = books.toSet
for {
  b1 <- bookSet
  b2 <- bookSet
  if b1 != b2
  a1 <- b1.authors
  a2 <- b2.authors
  if a1 == a2
} yield a1
```
A very clever way of writing!  
Note that the output of for loop is `bookSet`.
Other languages will take much longer lines. (iterator, ..)

### For-expression
When you have `map`, `flatMap`, and `withFilter`, we can use `for`.

### Map[T,S]
```val numerals = Map("I"->1, "V->5)```
Very useful.
Be careful when using `toMap`.

### Option
- Option[T] is as List[T] with at most element.
