# Testing

### Testing Frameworks for Java and Scala
Java
- JUnit
- Mockito (mostly used, used in Apache Spark)
- EasyMock
- jMock
- Powermock
- JMockit (has many functionalities, works well in Scala)
  - private members 
  
*Need to change a little bit, for Scala*

Scala
- ScalaCheck (inspired by the Haskell library Quickckeck)
  - property-based testing for Scala
- ScalaMock

### Approaches to Understanding
1. Testing => assures some conditions
2. Informal reasoning => results in invariants

=> Informal reasoning is more important! (TDD is not perfect, invariants are so tricky)

### Example

```
def foo(x, y) = x/y
```
Three scenarios:
1. bug
2. not a bug because caller is not supposed to give y = 0
3. not a bug because the author has verified => it is only a result of informal reasoning!

### Write assert{}/require{} rather than commenting
- in Scala, the condition checking function is much simpler
- Pros : no unit test required, faster code remind

### Examples of Invariants -- Connecting two modules

### Examples of Invaraints -- Loop invariants
```
while() {
  assert { loop invariant }
}
```

### Examples of Invarints -- Threads
```
assert { Thread.holdsLock(someLock) }
```
Informal reasoning on concurrency control

### AssertionError
Thinking Process
1. According to design, the invariant must hold
2. But it fails!
3. There must be something wrong
4. Now lets backtrace and fix the bug

### Strong invariants
ex. invariants connecting two modules

### Set of invariants reaches a critical mass
- Many many invariants makes a powerful code.  
- Once we have enough assertions, now we can afford aggressively optimizing the 
- Much easier and safer when extending/modifying modules

=> Brings an evidence for another action

### Integration Tests
- Involve all the components in the system
  - cli, master worker, ..
- Designate one or more waypoints in the execution path
- However, integration test itself is very hard, and requires an amount of design

### System Tests
- Assume production requirements
  - (e.g.) running process is killed, communication with a node suddenly fails, running node crashes
- Stress tests
  - (e.g.) use skewed data
