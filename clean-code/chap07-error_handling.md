# Error Handling

### Overview
> Error handling is important, *but if it obscures logic, it's wrong*.

An example of good error handling.
```java

public class DeviceController {
    public void sendShutDown() {
        try {
            tryToShutDown();
        } catch (DeviceShutDownError e) {
            logger.log(e);
        }
    }
    private void tryToShutDown() throws DeviceShutDownError {
        DeviceHandle handle = getHandle(DEV1);
        DeviceRecord record = retrieveDeviceRecord(handle);
        pauseDevice(handle);
        clearDeviceWorkQueue(handle);
        closeDevice(handle);
}
private DeviceHandle getHandle(DeviceID id) {
    ...
    throw new DeviceShutDownError("Invalid handle for: " + id.toString());
    ...
}
```

### A Very good test pipeline!!!
Write `try-catch-finally` statement first.
ex.
1. Make a unit test that shows that we'll get an exception when file doesn't exist.
2. First implement our execution code that catches `Exception`.
```java
public doSomething(String name){
    try {
        ...
    } catch (Exception e) {
        throw new StorageException("msg", e)
    }
    return blabla
}
```
3. If test passes from step 2, match the real type of exception: `FileNotFoundException`.
```java
public doSomething(String name){
    try {
        ...
    } catch (FileNotFoundException e) {
        throw new StorageException("msg", e)
    }
    return blabla
}
```
Much better and precise!


### Use Unchecked Exception
def) Checked exception : A forced, compile-time exception that must be handled. In JAVA, it does not inherit `RuntimeException`. [reference](https://madplay.github.io/post/java-checked-unchecked-exceptions)

Using checked exception is very **costly**. That is, if a small exception logic has changed, we need to change all following logics along function call stacks. When implementing critical library, you must catch them.

Scala doesn't declar checked exception because of higher-order function.
Use 3rd party library, `no-exceptions` in scala to handl exceptions. 
`throws SomeException` in Java : `@SomeException`(decorator) in scala.

### Provide context message with Exceptions
```
try {
        ...
    } catch (FileNotFoundException e) {
        throw new StorageException("CONTEXT!!!", e)
    }
```
Plus, add error to logging!

### Define excpetion in terms of Caller's Needs
- Multiple `catch`es in a single try-catch statement should have same exception level.
- If not possible, consider to wrap third-party APIs.

### Define the normal flow
It is good to have a superclass to throw general-case exceptions, rather than leaving child class to handle each time. 
