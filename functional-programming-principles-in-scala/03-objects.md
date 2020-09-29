# Objects

## OOP in Sccala

### lazy val

- val : eager, CBV  
- def : lazy, CBN  
- lazy val : lazy, Call-By-Need

Injudicious usage of `lazy val` results in program overhead and somtimes even deadlock.

### Auxiliary Constructors

Scala allows only **1** constructor. If extra needed, call auxiliary constructors.

### Classes

- Superclass, Subclass, Base Class
- `abstract class AbsClass` / `class SubClass extends AbsClass`

### Subclass

When to introduce subclass?
- It is very important to keep concise class architecture.
- Too many classes results in big complexity of the code. Subclass is **not always good**.

Back to OCaML
```ocaml
type IntSet = 
  Empty
| NonEmpty of int * intSet * intSet
```
would result in class hierarchy of,
```
abstract class IntSet {}
class Empty extends IntSet {}
class NonEmpty extends IntSet (int, intSet, intSet) {}
```

### Traits
It tooks long time to conclude, to indroduce **trait** is the right answer.  
Other candidates : Diamond inheritence in C++, Single superclass in JAVA. But they all failed to gain flexibility.

Try to look for **stackable traits** [link](). It elegantly implements decorator patterns.

Class vs Traits
- A class can have only one superclass.
- You can use several traits to express different properties.
- (Traits have a little performance issues, thousands of calls per sec would affect the performance)
- **Prefer traits to abstract classes**

### Scala Class Hierarchy
```
scala.Any
  scala.AnyRef (use pointers, starts from 24 bytes minimum)
    scala.Iterable
    scala.String
    other java classes
    ...
      (all have scala.Null as subclass)
  scala.AnyVal
    scala.Double
    Scala.Unit
    ...

Every subclasses of scala.AnyRef have scala.Null as its subclass.
Every classes have scala.Nothing as its subclass.
```

### Nothing Class
- Uninhabited (void)
- Useful in several ways
  - e.g. Nil : List[Nothing]
  - e.g. Whenever A <: B, List[A] <: List[B] (design choice of scala.List)
  - (refer to subtyping - covariant and contravariant in PL theory)

### Why scala is so powerful
- It integrates **ADT in FP** and **Class Hierarchy in OOP** so naturally (it's a convention of introducing a class)
- High order of Type handling

### Type Parameters
- `pair[Int]()`, `pair()`
- Of course, scala somehow automatically inferences the type.

## Questions
What is the real power of **OOP**?
What is the real power of **FP**?
What is the real power of **Type Theory**?
What is the real power of **Traits**?
