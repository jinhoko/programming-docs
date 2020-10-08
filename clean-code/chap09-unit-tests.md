# Unit Tests

### Many ways of software development
- Waterfall Model
- Test-Last Development
- TDD (Test Driven Development)
- Agile

### What is Unit Testing?
A suite of simple tests for validating the proper execution of target codes

### The reality of Unit Testing

#### The three basics of TDD
1. Do not write production until you write failing unit test code.
2. Unit test should be concise.
3. The coverage of production should not exceed that of unit tests.

#### Keep Tests Clean
- Do ONE thing. 
  - Single assertation per test.
  - Single concept per test.
- Take care of readability ; Anybody can also read your tests!
- Test code is just as important as production code ; requires the same pipeline with the production code.
- Oversized tests would lead to daunting management problem

### Writing Tests

#### Methodology
- Follow the *given-when-then* convention in your test.
- Also eleminate duplicates by using *template method* pattern.

#### Summary


FIRST
- Fast : Test should be fast, so that we can run frequently
- Independent : Each should be independent. One test should not set up conditions for the next test.
- Repeatable : Test should be repeatable and consistent in any environment.
- Self-validationg : Test itself should have a boolean output.
- Timely : Know the right thme to write & execute your test.
