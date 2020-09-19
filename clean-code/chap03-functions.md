# Functions

### Simple function is always good
- Once you develop your function, it gets bigger and bigger.
  - You must continuously reorganize the function structure
- Refer to Databricks Spark Scala Guide [link](https://github.com/databricks/scala-style-guide#naming)
  - <30 lines in a function is the best.
  
### DO ONE THING ; command-query seperation
- That is, just only do what the name indicates
- if the function is dealing both command and query, so the name should
  - e.g. `decrementAndReturnIfZero()`

### Use descriptive names
- e.g. `obtainSomethingAndElseToReturnThis()`

### In switch statements
- try to use `enum` types for easy comprehension

### Arguments
- In scala, try to use named argument when the function has multiple arguments with same type
- Good arguments requires a lot of conceptual power
  - **Order, Type, Options**
- Output arguments is even harder

### # of Arguments
- 1: useful when in/out type matches ; transformation operation
- 2: ordering problem, especially when comparing the two?
- 3: harder!
- Reducing # arguments by introducing a class is a good practice

### Exception Handling
- A must-do practice
- Define error codes (object or enum) in your own way

### Extract try-catch blocks
```
def wrapperFunction():
  try:
    innerFunction()
  catch:
    (excpetional flow)
```

### Structured programming
- Only 1 return statement
- No break/continue statement
- Every control flow must follow the structure!

### RENAME / SPLIT / CHANGE NAME / SHRINK / REORDER!
