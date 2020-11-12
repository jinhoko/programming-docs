# Out of the Tar Pit

### 1. Introduction 

The contents of the paper will help simplifying the construction of large-scale software systems.   
*(perhaps with ideas combining with the relational database world!)*

### 2. Complexity

What makes building software hard : **Complexity, Conformity, Changeability and Invisibility**, and complexity is definitely the root cause. Being able to think and reason about our systems is crucial. 

> (Hoare, 1980) The price of realibility is the pursuit of utmost simplicity. ... Two ways of constructing a software design : one is to make it so simple that there are no deficiencies, and other is to make it so complicated so that there are no obvious deficiencies. First one is much harder.


### 3. How to UNDERSTAND a system

Two widely-used approaches
- Testing : black-box approach ; infer from the input and output
- Informal Reasoning : examining from the inside ; extra info available

> (O'Keefe, 1990) Those who want really realiable software will discover that they must find means of avoiding the majority of bugs to start with.

Problem with testing
1. Gives you nothing
2. Can give you different results based on different inputs
=> Have you performed the right tests?

Conclusion : all methods of understanding have its shortcomings (even the informal reasoning)

### 4. Causes of Complexity

#### 4.1. Complexity caused by state

> (Brooks, 1986) Every computer and computer software have numerous states. (Orders-of-magnitude more states for softwares!) Each state might yield different outputs, making testing so hard.

State := mutable state specifically. (variables, not value)

Impact of state on **testing** : the common approach is to start from the beginning. It is however not always possible. The problem is that testing for *one set of inputs* tells you nothing at all about the behaviour of different *set of inputs*.

Impact of state on **informal reasoning** : results in case-by-case mental simulation. ('if... then... otherwise... and that as well.. blablabla'). The number of considerations grow exponentially. Consider, if a stateless procedure is dependent to the stateful procedure, it becomes a stateful procedure as well.

What we have to do : **limit and manage** the state.

#### 4.2. Complexity caused by Control

The difficulty is that when control is an implicit part of the language (as it always is). When a programmer codes, he/she must be forced to specify **how** the system should work(in the matter of context) but **not simply what** is desired. Hence they are forced to over-specify the problem. 

These behavior makes reader to infer the 'how's of a programmer. The program is ought to be written in some order (in a imperative manner).

Another control-related problem : concurrency (that affects testing as well). Common model is 'shared-state concurrency', that specifies the explicit control synchronization.

#### 4.3. Complexity caused by Code Volume

> (Brooks, 1986) Many of the classic problems developing software products derivce from this essential complexity and its nonlinear increase with size.  
> (Djikstra, 1972) ... there is some kind of law of nature telling us that intellectual effort needed grows with the square of program length. 

#### 4.4. Other types of Complexity causes

Dead code, unnecessary (data) abstraction
