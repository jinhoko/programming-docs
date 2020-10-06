# Types and Pattern Matching

### List
```
type 'a list = 
  Nil
| Cons of `a * `a list
```


### 'apply' method in scala
- f(a) is expanded to f.apply(a)
- f(a, b) is expanded to f.apply(a, b)

### apply method for Factory Patterns


### Subtyping and Type Bounds
**A is subtype of B** if an expr of type A is used wherever an expr of type B is expected.

```
def assertAllPos[S <: Intset]
```
S should be bounded to subclass of IntSet!

### Variance when A<:B
- Definition
C[A] <: C[B] - C is covariant
C[A] >: C[B] - C is contravariant
neither      - C is nonvariant
- Declaration in Scala
class C[+A] {}
class C[-A] {}
class C[A] {}

### 


### Why Covariance?
- in JAVA, no concept of covariance ; thus implement
  - in Java, covariance is prohibited! counterintuitive. (e.g. List<String> is not a subtype of List<Object>)
  - refer to p.134 in book Effective Java *(item 28 : use bounded wildcards to increase API flexibility)*
- Code becomes much simpler in Scala, with introduction of covariant.


### Case Classes and Pattern Matching

```
trait Expr
case class Number(n: Int) extends Expr
case class Sum(e1: Expr, e2: Expr) extends Expr
```
Case class e
```
def eval(e: Expr): Int = e match {
  case Number(n) => n
  case Sum(e1,e2) => eval(e1) + eval(e2)
}
```
- With `case class`, `equals()` method is automatically/correctly created!
- It is indeed very very complicated to implement `equals` with JAVA.
