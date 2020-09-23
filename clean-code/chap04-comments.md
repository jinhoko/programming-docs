# Comments

### Proper use of comment
> The proper use of comments is to compensate for our failure to express ourself in code.
- Codes change, but comments don't most of the times.
- Rather focus on making clean codes!

### Explain with code
```java
if ((employee.flags & HOURLY_FLAG) &&
(employee.age > 65))
```
Bad
```java
if (employee.isEligibleForFullBenefits())
```
Better!

### Good, Necessary Comments

##### Legal 

Copyright or License(MIT, GNU, ...). 

##### Informative

Explanation on the abstract method, header, interface, function definition.
```java
// Returns an blabla of blabla.
protected abstract ClassName classMethod();
```
Also, it is good to comment on things such as textual format, enum types.

##### Clarification
Clarify intent. Use with caution, for instance, use only when implementaing a standard library.

##### Warning
To warn the code users to carefully use the code!
Q : wouln't it be good to raise warning such as `DeprecationWarning`, or so?

##### TODO
Use only for your development!

### Must-avoid Comments

##### Mandated Comments
It is silly to put all docs comment in front of function/class declaration.

##### Rather write a chain of comments
```java
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```
Bad.
```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```
Better!