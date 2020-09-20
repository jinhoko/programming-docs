# Functional Programming

### FP Core

##### Eager evaluation `val` vs Lazy evaluation `def`
```scala
val a = {
  println("compute 7!")
  3 + 4
}
def b = {
  println("compute 7!")
  3 + 4
}
```
*(Eager evaluation refers to most of programming convention in imperative programming, 
while lazy evaluation can be thought of textual substitution, literally)*

##### Call-by-value vs Call-by-name
```scala
def double(x: Int): Int = x + x      // CBV
def doubleN(x: => Int): Int = x + x  // CBN

> double(c)
computing 7
14
> doubleN(c)
computing 7
computing 7
14
```
*(It is more natural to use `def` and CBN together)*

Know when to use `val` and `def`+CBN. It makes your program much simple and clear.
It is very important to estimate the actual timing of when the variable is evaluated.

### Recursion

##### Tail recursion
```scala
@tailrec
def gcd(a: Int, b: Int): Int
  if (b==0) a else gcd(b, a%b)
```
The `@tailrec` decorator is ensured the function is tail recursive by compiler.
