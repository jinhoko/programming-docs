# How To Design A Good API and Why it Matters

* source :  [https://www.youtube.com/watch?v=heh4OeB9A\-c](https://www.youtube.com/watch?v=heh4OeB9A-c)
* pdf : [https://github.com/jinhoko/programming\-docs/blob/master/api\-design/How%20to%20Design%20a%20Good%20API%20and%20Why%20it%20Matters.pdf](https://github.com/jinhoko/programming-docs/blob/master/api-design/How%20to%20Design%20a%20Good%20API%20and%20Why%20it%20Matters.pdf)

Why is API design important?

* for customers
    * Company's greatest assets : customers invest heavily on buy/write/learning APIs
    * Can be company's liabilities : aBad API leads to stream of support calls
* for you
    * If you are programmer =\> you are API design
        * good code is moduled, API connects between modules
        * so good coder is a good API designer
    * modules become reusable
* language design == API design

Good API

* Easy to learn, use w.o. docs
* Hard to misuse
* "Sufficiently" Powerful \(not just powerful, but powerful enough\)
* Easy to extend
* Appropriate to audience \(who's using?\)

## I. Process of API Design

Gather Requirements

* Gather\! but with skepticism
    * only gather the 'goal', not the 'method'
    * you decide the optimal method
* Extract true requirements : from use\-cases
* Better if you even draw bigger picture than the given requirements

Start with small steps : short 1 page draft

* repeat : get multiple feedbacks and modify
* flesh it out as you gain confidence
    * this necessarily involves virtual coding

Write to your API early and often

* virtually start using your API even implementing it\!
    * saves you from wasting time
* the code lives on examples and unit tests

Writing to SPI is even more important

* SPI : Service Provider Interface
    * plug\-in interface enabling multiple impls

Maintain Realistic Expectations

* most API designs are over\-constrained
    * you cannot please everyone, but stick to unified, strong rules
* expect users to make mistakes \-\> and evolve them

## II. General Principles

Should do one thing and do it well

* functionality should be easy to explain
    * provide good names\!
    * good names drive good designs \(design functions, member variables, ...\)
    * make it portable

Should be as small as possible but no smaller

* When in doubt, leave it out \(very important\)
    * better add design later, but impossible to deprecate
* Conceptual weight is more important
    * e.g. TreeSet, HashSet, ConcurrentSet, ... , but no one cares cuz they share same concepts

Implementation should not impact API

* impl details should strictly be hidden to users
    * users cannot see nor change
    * to do so, be aware of what is an impl detail
        * e.g.1.  don't specify hash functions
        * e.g.2. all tuning parameters \(do these need to be exposed???\)
* do not impl details leak into API
    * e.g. once api is serializable, all private fields go public

Minimize accessibility

* information hiding
    * set members private as possible
    * public classes should have no public fields
* remove dependencies between modules

Names matter \- API is a language

* Names should be self\-explanatory
* Be consistent \- same word means same thing
    * e.g. remove vs delete? 
* Be regular \- symmetry
    * e.g. addKey\(\) \<\> deleteKey\(\)

Documentation matters

* _Reuse is something that is far easier to say than to do. Doing it requires both good design and very good documentation. Even when we see good design, which is still infrequently, we won't see the components reused without good documentation._

Document religiously\!, but no one's doing it.

* Document every class / interface / method / ... and exception
    * class : what an instance represents
    * method : pre/post conditions, side\-effects
    * parameter : units, form, ownership
    * variables : mutable or not?

Consider performance consequence of API design decisions

* \(according to effective Java\) Premature optimization is evil.
* But you should never ignore it
    * e.g. unnecessarily making mutable
* do not warp API to gain performance
    * good design usually coincides with good performance

API must coexist peacefully with platform

* Do what is customary for the platform
    * Fit in the standard naming conventions
    * Avoid obsolete parameters
* DO NOT transliterate APIs. If doing so, they broke eventually.
    * C\+\+ \!= JAVA, the classes do not have to be same.

## III. Class Design

Minimize Mutability

* Classes should be immutable unless there's a good reason to be mutable
* If it must be mutable, keep state\-space small, well defined

Subclass only where it makes sense

* subclass implies substitutability
    * only 'is\-a' relationship
    * otherwise, use composition
* Bad : Properties extends Hashtable / Good : Set extends Collection

Design and document for inheritance or else prohibit

* Inheritance violates encapsulation
    * When superclass modified, it modifies subclass

## IV. Method Design

Don't make the client do anything module could do

* reduce need for boilerplate code

Don't Violate the principle of least astonishment

* API user should not be surprised by its behavior

Fail fast \- Report Error as soon as possible

* Compile\-time is the best : static typing, generics
* At runtime, method should be failure\-atomic
    * if fails, make it did nothing\!

Provide Programmatic access to all data available in string form

* e.g. getFileName\(\), ..
* user should not parse debugstring

Overload with care

* avoid ambiguous overloading
    * to be conservative, no two with same \#args
* Often better with different name
* If you must provide overloading, ensure same behavior for same arguments.
    * e.g. TreeSet\(Collection c\), TreeSet\(SortedSet s\), ... ignores/respects ordering
        * what if SortedSet is casted into Collection?

Use appropriate parameter and return types

* interface \> classes for input
* specify input param type
* don't use string if better type exists

## V. Exception Design

Use consistent parameter ordering accross methods

* important if param types identical
    * e.g. \<string.h\> : strcpy\(dest,src\) / bcopy\(src, dst\)

Avoid long parameter lists

* if long, 1\) break up method or 2\) create helper class to hold parameters

Avoid return values that demand exceptional processing

* user should not handle exceptions that are not specified
    * e.g. null values?

Throw exceptions to indicate exceptional conditions

Favor unchecked exceptions over checked exceptions

Include failure\-capture information in exceptions
