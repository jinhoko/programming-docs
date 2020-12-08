# Design Patterns - Lecture 4

## Dependency Injection

### Introduction

The client requires a service, but does not build it. We pass the service to client  
(Service : dependency / Client : dependent / inject via interface)

### 3 Types of Dependency Injection

- Constructor injection
```
Client( service ) {
  this.service = service
}
```
We can pass different service object to userservice.  
But user should implement all wrapper functions of the service interface.  
To ineffective!

- Setter injection
```
void setService( service) {
  this.service = service
}
```
- Interface injection
Provides an injector method that injects itself to clients

### Self-type annotation vs Inheritance
- Self-type annotation
```
trait A
trait B { this: A => ... }
```
B can access methods in A, **without leaking** the method.  
We can set multiple types (A1, A2 ..)

- Inheritance
```
trait A
trait B extends A
```
This has leaking problem

### Leak
```
trait B extends A
trait C extends B with A
```
Assume A is a service, and B is client.  
There exists a chance for C to access A's methods, which is invalid.  
However, self-type annotation can prevent this

## Typical Usage - Cake Pattern
```
trait Repository {
  def save(user: String) : Unit
}

trait DatabaseRepository extends Repository {
  def save(user: String): Unit = {
    println("success!")
  }
}

trait UserService {self.Repository =>
  def create(user: String): Unit = {
    println("created")
    save(user)
  }
}
```
`new UserService` => invalid, because repository is not provided.  
`new UserService with DatabaseRepository` => OK! we assign the repository

```
x.create("name")
x.save("name")
```

This pattern is very strong due to object composition. (rather than inheritance)  
*example: EmailService cannot access DB. but can access UserDB. In inheritance, emailservice can access DB, which violates the separation*

## Dependency Injection in many levels
- functions, objects, modules, subprojects


## Dependency Injection in Commercial Products
- Scala itself is powerful enough
- Java utilizes Spring framework for handling dependency injection problem
