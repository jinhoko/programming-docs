# Design Patterns - Lecture 1

## What is Design Pattern?
- A set of solutions toq commonly required design techniques.
- Scala is very flexible!
  - supports first class function
  - by-name parameter
  - lazy evaluation

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
Very flexible, but be very careful in using. (howitworks) (if implicit class found, automatically convert the object!)

### Decorator
Extends the functionality of an **`object`**, not a class, without creating a subclass.  
The order of stacking matters in the result!

Decorator enables **COMPOSITION** of functions, applied to object.

Java way : intermediate decorator class is used
```
interface Shape
  class Circle
  class Box (draw())
  abstract class ShapeDecorator => intermediate decorator!
    class ColorDecorator
    class LineDecorator
```
```
Shape circle = new circle
Shape colorCircle = new ColorDecorator(circle)
Shape lineColorCircle = new LineDecorator(circle)
```

Scala way : Stackable traits
```
trait A {}
trait B extends A {}
....
```
```
val circle = new Circle
val colorCircle = new Circle with Color
val lineColorCircle = new Circle with Line with Color

stack order => Color -> Line -> Circle
```

##### example : EventHandler : Sync/Async

```
trait EventHandler[E] {
  def foo()
  def bar()
}
trait SyncHandling[E] extends EventHandler[E] {   => These stackable traits are decorators!

}
trait AsyncHandling[E] extends EventHandler[E] {  => These stackable traits are decorators!

}

class AMContainerMap () extends EventHandler {}

amContainerMap = new AMC with AsyncHandling       => Async AMC!
amContainerMap2 = new AMC with SyncHandling       => Sync AMC!
```
With stackable traits, we do not have to define AMContainerMap as as subclass of one of sync/async.    
We will rather select its type in instantiation time, with the use of stackable traits.

**One of the privileges of Scala language!**
