# Out of the Tar Pit


## 1. Introduction 

The contents of the paper will help simplifying the construction of large-scale software systems.   
*(perhaps with ideas combining with the relational database world!)*


## 2. Complexity

What makes building software hard : **Complexity, Conformity, Changeability and Invisibility**, and complexity is definitely the root cause. Being able to think and reason about our systems is crucial. 

> (Hoare, 1980) The price of realibility is the pursuit of utmost simplicity. ... Two ways of constructing a software design : one is to make it so simple that there are no deficiencies, and other is to make it so complicated so that there are no obvious deficiencies. First one is much harder.


## 3. How to understand a system

Two widely-used approaches
- Testing : black-box approach ; infer from the input and output
- Informal Reasoning : examining from the inside ; extra info available

> (O'Keefe, 1990) Those who want really realiable software will discover that they must find means of avoiding the majority of bugs to start with.

Problem with testing
1. Gives you nothing
2. Can give you different results based on different inputs
=> Have you performed the right tests? / Reason why TDD alone is not enough.

Informal reasoning is about finding invariants. => Always write invariants in codes!

Conclusion : all methods of understanding have its shortcomings (even the informal reasoning)


## 4. Causes of Complexity

### 4.1. Complexity caused by state

> (Brooks, 1986) Every computer and computer software have numerous states. (Orders-of-magnitude more states for softwares!) Each state might yield different outputs, making testing so hard.

State := mutable state specifically. ( (global) variables, not value)

Impact of state on **testing** : the common approach is to start from the beginning. It is however not always possible. The problem is that testing for *one set of inputs* tells you nothing at all about the behaviour of different *set of inputs*.

Impact of state on **informal reasoning** : results in case-by-case mental simulation. ('if... then... otherwise... and that as well.. blablabla'). The number of considerations grow exponentially. Consider, if a stateless procedure is dependent to the stateful procedure, it becomes a stateful procedure as well.

What we have to do : **limit and manage** the state.

### 4.2. Complexity caused by Control

The difficulty is that when control is an implicit part of the language (as it always is). When a programmer codes, he/she must be forced to specify **how** the system should work(in the matter of context) but **not simply what** is desired. Hence they are forced to over-specify the problem. 

These behavior makes reader to infer the 'how's of a programmer. The program is ought to be written in some order (in a imperative manner).

Another control-related problem : concurrency (that affects testing as well). Common model is 'shared-state concurrency', that specifies the explicit control synchronization.

### 4.3. Complexity caused by Code Volume

> (Brooks, 1986) Many of the classic problems developing software products derivce from this essential complexity and its nonlinear increase with size.  
> (Djikstra, 1972) ... there is some kind of law of nature telling us that intellectual effort needed grows with the square of program length. 

### 4.4. Other types of Complexity causes

Dead code, unnecessary (data) abstraction

### Conclusion : Complexity breeds complexity, Simplicity is Hard, Power corrupts

## 5. Classic approaches to managing complexity

### 5.1. Object-orientation

It has evolved as the dominant method of general software development of traditional computers, and many of its characteristics spring from a desire to facilitate state-based computation.

**State**
- Object => some states & set of procedures accessing and manipulating that state
- Problem with OOP : encapsulation based integrity constraint is strongly biased toward single-object contstraints. 
- Object identity : can be considered to ba a rejection of the relational algebra. => forced to adopt creation of value objects.

**Control**
- Achieves concurrency control with message-passing model

=> OOP suffers greatly from state-derived and control-derived complexity.

### 5.2. Functional programming

FP has its roots in completely stateless lambda calculus. The untyped lambda calculus is known to be equivalent in power to the standard stateful abstraction of compution : the Turing machine.

**State**
- It avoids state and gains property of *referential transparancy*.
- Informal reasoning gets effective.
- Encourages a more abstract use of control (fold, map, filter, foreach)

**Kinds of state**
- Achieve state by passing extra parameters to the procedure. 
- Use functional values to stimulate state.

There is no reason why the functional sytyle of programming cannot be adopted in stateful languages => Birth of scala language?

### 5.3. Logic Programming

.

## 6. Accidents and Essence

Two types of complexity :
- Essential complexity : relies in the essence of the problem
- Accidental complexity : is all the rest : one developers would not take in an ideal world

> What is essential to the dev team is what the users have to do be concerned with.
*(One following implication of the definition is, if the user don't even know about what something is, that is never a essential complexity.)*

 
## 7. Recommended General Approach

The complexity could not possibly be avoided even in the real world. Try to reduce much accidental complexity as much as possible.

### 7.1. Ideal world

- First step : informal requirements -> formal requirements
- Goal : Minimize accidental state.
- Classify data (into 4 types) ; refer to the following image
 - Try to only leave essential state.
- Control : is enirely accidental.

![image1](https://github.com/dgggit/dist/blob/master/out-of-the-tar-pit/image1.png?raw=true)


### 7.2,3. Real world and Recommendations
- Required accidental complexity in the real world
 - 1. for performance (e.g. cache)
 - 2. for ease of expression (e.g. data derived from a whole series of user inputs **and** previous values

Recommendation : separate and avoid
![image2](https://github.com/dgggit/dist/blob/master/out-of-the-tar-pit/image2.png?raw=true)

As a result, **seperation** is critical for avoiding complexity.

## 7.3. Separation
Follow the steps :
1. Essential state first ; data (representation) first
2. Essential logic ; business logic
3. Accidental state and control 

Look for the arrows in the image! The direction of the arrows must be followed. 
![image3](https://github.com/dgggit/dist/blob/master/out-of-the-tar-pit/image3.png?raw=true)

