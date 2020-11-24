# Lecture 2

### Future[T]

> Building block of communication. It can be thought as a pointer to the thread.
> The variable of type T may not be available now, but might be in the future.
> (Baker & Hewitt, 1977)

Creating the object itself returns immediately, but the thread runs in background.  
The programmer is responsible for explicitly dereferencing the object.

### Progress

- Once `Future` is spawned, 2 concurrent threads starts to run
- main thread constantly checks if the Future is completed
- fetch value after finishes

### Future Callbacks

```
def some() : Future[] = {}
def any : some()

any foreach { }
```
After Future thread finishes, **new thread** is generated to execute foreach statenment.  
It is basically utilizing the composibility of computer science.

### Exception in Future
```
val some : Future[] = Future {}
some.failed foreach {}
```
foreach statement is executed on exception

### More on Futres
- Note : Fatal Exceptions in Future are not caught. You must explicitly handle these error in the main thread's context.
  - OOMError
  - VM Error

### Promise[T]
- Single-assignment variables
  - You can assign the value just once
- Promise.future

### Seperation of Concerns (composibility)
1. Describe **when** the action should be taken
2. Describe **the action** to be taken when triggered.

The 2 concerns can be seperated, and are connected via promise.

### Example : Future.or
- Effectively extends the Future standard library.

## References
https://www.baeldung.com/scala/futures-promises

