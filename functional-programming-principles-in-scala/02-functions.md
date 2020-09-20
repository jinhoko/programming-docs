# Functions

### FP in Scala

##### Higher order functions
Function that takes function as an input
```scala
def sum(f: Int=>Int, a: Int, b: Int):Int = {}
```
Currying
```scala
def sum(f: Int=>Int)(a: Int, b: Int):Int = 
  if (a>b) 0 else f(a) + sum(f)(a+1, b)
(Int => Int) => (Int, Int) => Int
```

##### Infix notation
```
<object> <method> <argument> ,,,
<object>.<method>(<argument>)
r.add(s)
r add s
```
Scala supports both. Just be consistent with your choice.  
**Method** and **Function** is different! Only method choice allows infix notation w. object level.

##### Annonymous functions
```scala
l.map(x => 2*x)
l.map(2 * _)
sum2(x, y => x+y)
sum2(_ + _)
```
Underscore `_` refers to each provided argument, sequentially.

### OOP in Scala

##### Basics
```scala
class Rational(x:Int, y:Int) {      // In Scala, Only 1 constructor per class is possible.
  def numer = x
  def denom = y
  
  override def toString: String =   // Must add 'override' keyword to rewrite existing member
    numer + "/" + denom             // in the superclass.
  
new Rational(1, 2)
```
##### Self-Reference
```scala
...
private def value = x
this.value            // This limits the namespace only to the member of the object. 
...
```
However, other objects within same **class** can access `value` (that is how `private` keyword works in C++).
To prevent this, scala introduces a new limiter, `private[this]`, that only allows its access to the member of the same **object**.
```scala
...
private[this] def value = x
this.value           
...
```
##### Essence of OOP
- Multiple representation(dynamic dispatch) ; Sharing a same ADT within two different class.
- Encapsulation
- Subtyping
- Inheritance
- Self-reference

### Assertion
```scala
assert{expr}    // state invariants on your code. can be disabled
require{expr}   // Fault goes to the user of the code. cannot be disabled.
ensuring{expr}  // Fault goes to code writer. cannot be disabled.
```
