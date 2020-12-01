# Design Patterns - Lecture 2

## Value Object

#### Equality : equal if all members are equal

```
Point a = new Point(1, 2)
Point b = new Point(1, 2)

a.equals(b) => true!
```
With the help of case class and immutable(`val`) definition  
Very useful in concurrent programming! Ex. money, transactions, ....

#### Value Object in Scala
```
val point = (1, 2)
case class Rectangle() {}
```
Use tuples and case classes, because equals(), hashCode(), toString() is automatically generated.  
It is much better to keep the items immutable.

#### Value object in JAVA  
-> requires overriding of 2 functions, `equals` and `hashCode`
```
class A() {
  bool equals()   => error prone!
  int hashCode()  => error prone!
}
```
> Object Equality is very very tricky to implement!

## 
