# Streams and Lazy Evaluation

### Streams

- A stream is a **list** whose tail is evaluated only on **demand**.
  - can be infinite or finite (don't care)
  
### List vs Streams

- Are basically same in structure
- Differences :
```
type 'a list = Nil | Cons of 'a * 'a list
type 'a stream = Nil | Cons of 'a * (unit -> 'a stream)
```
Computation is delayed by introducing a closure

### Lazy initialization in Scala
```
lazy val x = expr
```
Like call-by-need.
It is powerful in scala because it is thread-safe.

### Lazy initialization in Java
- How many lines of Java code you need to implement lazy eval in Java? => 10+ lines
  - Needs `double-locking` design pattern + volatile class => Because Test-and-set in JAVA is not atomic.
- Concurrent programming requires deep understanding of memory model of that language.

### Infinite Streams
