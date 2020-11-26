# Design Patterns - Lecture 1

## Creational Patterns
- Factory method
- Lazy initialization
- Singleton

### Factory Method
- interface for creating objects
- Use companion objects (`object Foo { apply() }`) in Scala
```
object Animal { def apply () { new Foo() }  }
Animal() // generates new object!
```
Benifits?
- caching objects (e.g. memoization)
- integrated management of objects
  - flexible to interface changes
  
### Lazy Initialization
- Without `lazy val`, we need 'double-checked locking'
- must avoid cyclic dependencies between lazy values
- do not blocking operations in lazy value init or singleton object constructors
- otherwise, all leads to deadlock

### Singleton
- def) generate only one copy of the object
- Directly supported in scala (`object Foo` : thread-safe, uses lazy init)
- In Java, we make constructor as private and alternatively calls `getInstance()` to return the same instance

## Structural Patterns
- Adaptor (`implicit class` in scala)
- Decorator (stackable `trait` in scala)

### Adaptor
- converts the interface of a class into another interface

Java way
```
public interface Log { void warning(), void error() }
log = new LoggerToLogAdapter( new Logger() )
```
=> Users only calls the adaptor

Scala way
```
trait Log { def warning(), def error() }
final class Logger { def log() }
implicit class LoggerToLogAdaper(logger: Logger) extends Log {
  def warning = { logger.log( WARNING, msg) }
  def error = {}
}
val log = new Logger()
```
Gets `logger:Logger` and converts to `Log`  
Very flexible, but be very careful in using.

### Decorator

