# Design Patterns - Lecture 3

## Chain of Responsibility

Decouples:
- sender of a request
- handle of the request

Multiple handlers are allowed to form a chain. 

```
Sender -> Handler -> Handler -> ....
```
It can be viewed as a composition of requests!  
We must discover the situation when CoR is necessary, or much convinent.

### Implementing CoR

- Every handler inherits a base interface
- A handler contains an optional reference to the next handler

### CoR in Java
```
public abstract class EventHandler {
  setNext( ) { next = handler; }
  public void handler( ) {
    if canHandle, doHandle
    else if next != null, next.handler();
  }
  bool canHandle(); -> override
  void doHandler(); -> override
}

execute handler request.
```

### Netty : A good example of CoR

NIO client-server framework for network applications  
Bi-directional CoR. (since request should be returned at some time.)

