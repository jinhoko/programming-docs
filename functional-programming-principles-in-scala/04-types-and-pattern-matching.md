# Types and Pattern Matching

### List
```ocaml
type 'a list = 
  Nil
| Cons of `a * `a list
```

### 'apply' method in scala
- f(a) is expanded to f.apply(a)
- f(a, b) is expanded to f.apply(a, b)

### apply method for Factory Patterns
def) factory pattern method : subclass decides what class instance , without letting the parent class know the generated instance type. [link1](https://ko.wikipedia.org/wiki/%ED%8C%A9%ED%86%A0%EB%A6%AC_%EB%A9%94%EC%84%9C%EB%93%9C_%ED%8C%A8%ED%84%B4) [link2](https://jusungpark.tistory.com/14)

### Subtyping and Type Bounds
**A is subtype of B** if an expr of type A is used wherever an expr of type B is expected.

```scala
def assertAllPos[S <: Intset](r: S): S = {}
```
S should be bounded to subclass of IntSet!

### Variance when A<:B
- Definition  
C[A] <: C[B] - C is covariant  
C[A] >: C[B] - C is contravariant  
neither      - C is nonvariant  
- Declaration in Scala
class C[+A] {} - C is covariant  
class C[-A] {} - C is contravariant  
class C[A] {}  - C is nonvariant

### Covariance in List
Would this work?
```scala
(suppose T<:U => List[T]<:List[U])

trait List[+T] {
  def prepend(elem:T): List[T] = {}
}

x : List[T]
y : List[U]
z : T
w : U

x.prepend(z) : List[T]
y.prepend(w) : List[U]
x.prepend(w) : ????
```
This would not work in the last case. Thus we add subtyping rule to `prepend()` in order to handle such case, as follows.
```scala
(suppose T<:U => List[T]<:List[U])

trait List[+T] {
  def prepend[U>:T](elem:U): List[U] = {}
}

x : List[T]
y : List[U]
z : T
w : U

x.prepend(z) : List[T]
y.prepend(w) : List[U]
x.prepend(w) : List[U]
```

### Why Covariance?
- in Java, no concept of covariance ; thus the user is responsible for the implementation
	- in Java, covariance is prohibited! counterintuitive. (e.g. List<String> is not a subtype of List<Object>)
	- refer to p.134 in book Effective Java *(item 28 : use bounded wildcards to increase API flexibility)*  

=> Code becomes much simpler in Scala, with the  introduction of covariant.


### Case Classes and Pattern Matching

```scala
trait Expr
case class Number(n: Int) extends Expr
case class Sum(e1: Expr, e2: Expr) extends Expr
```
Case class e
```scala
def eval(e: Expr): Int = e match {
  case Number(n) => n
  case Sum(e1,e2) => eval(e1) + eval(e2)
}
```
- With `case class`, `equals()` method is automatically/correctly created!
- It is indeed very very complicated to implement `equals` with JAVA.
