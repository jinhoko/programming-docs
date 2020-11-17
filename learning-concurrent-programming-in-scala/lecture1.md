# Overview of JVM Memory Model


### Introduction

- Process : unit of launch from the viewpoint of OS
  - each process maintains isolated memory space
- Thread : unit of execution within processes
  - All threads share same process => needs concurrency
  - Assume OS threads, as opposed to user-level threads(maintained by user level library ; e.g. Green Threads in early Java)
  
### happens-before-relation in Java Memory Model

- Regarding visibility of write effects (assure write-after-read)

### happens-before #1 : Program order
Each action in a thread happens-before every other subsequent action in same thread.

### happens-before #2 : Transitivity
if A -> B -> C, then A -> C

### happens-before #3 : Volatile fields
Each time the variable must be stored/read from the main memory (invalidates cache!) (ref: [link](https://nesoy.github.io/articles/2018-06/Java-volatile))  
Note that, **volatie vs atomic vs synchronized** is all different. (ref : [link](https://mygumi.tistory.com/112))

### happens-before #4 : Monitor locking
```
Lock i = ~
i.lock()
try {

}
finally {
  i.unlock()
}
```
OR

synchronized block : `foo.synchronized { } `

This rule ensures that **unlock -> lock**, otherwise, deadlock.

### happens-before #5 : Thread start, thread termination
Each execution barrier located at thread start / join
