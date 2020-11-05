# Lecture 3

### Integrity

Apply same, strict rules in your every decision.
- Should be one mind OR group of agreeing minds.
- Someone should control the concepts

### Second-System Effect

How an **architect** can successfully influence implementation
- Remember that the buildter has creative responsibility for implementation => just suggest!
- Listen to the builder's suggestions for architecture improvement

The second system is prone to over-design : *it's a general tendency!*

### Passing the Word
- Even though design team is large, the results(writing) must be written by 1~2 person.
- One needs **1. Formal definition** for precision and **2. Prose definition** for comprehensibility
  - *first propose broader design, and then details!*

### Why Did the Tower of Babel Fail?
- Lack of (effective) communication
- In software engineering : **Project meetings / Shared formal workbook (e.g. github, slack!)**
  - Note that, everyone should access the material, but NOT the internals
  - For internals, only the interfaces!
- Sync vs Async Communication
  - Sync : Slack => might distract developers.
  - Async : JIRA, shared document => much preferred. quality of writing.
### Calling the Shot
- Effort to implement a program goes up as a magnitudes of program size.

### Ten Pounds in a Five-Pount Sack
- The implementation must always keep **consistency, clarity, and integrity** till the end.
  - Fast programs are result of overall stategic design (=algorithm).
  - The breakthrough will come from redoing **representation** of the data.
  
> How to represent the data?

### Plan to Throw One Away
- Perfect design is impossible => admit first
- Things are ought to change

#### (2 Steps forward and 1 step back)
- Some critical bugs are discoverd after long time.
- Remove side effects
  - Immutable objects
  - functional style
  - Global variable
  - How????????????????

### The Whole and the Parts
- System debugging takes very long
  - Use an automated script

### Hatching a Catastrophe
- Set up **milestones and dates**
  - Milestone is better when set to BINARY value
- Do not lie about milestone after once set

### Documentation
- Record "Why?"

### Epilogue : The tar pit of software engineering will continue EVER!
