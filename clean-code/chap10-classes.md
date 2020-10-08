# Classes

### Classes Should Be Small!
- if we cannot derive a concise name for a class, then it is likely to be large.
- Single Responsibility Principle : a class should have a **single** reason to change.

### Cohesion
- It is betteer when # of class variables are small
- While keeping less variables, try to let many functions refer the variable : cohesive!

### Inheritance
- It can violate the encapsulation (of the parent class)

### Favor Composition Over Inheritence
*(core concept of OOP, from the book Effective Java)*

(example)
> Inheritance : class Rectangle extends class ColoredRectangle  
> Composability : class ColoredObjects references class Rectangle and class Color

(core concept of computation thinking)
- divide and conquer
- inductive thinking
- composibility (aggregate small things to make bigger one)
