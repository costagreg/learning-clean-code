# Unit Tests

## The Three Laws of TDD

*First Law* You may not write production code until you have written a failing unit test

*Second Law* You may not write more of a unit test than is sufficient to fail, and not compiling is failing

*Third Law* You my not write more production code than is sufficient to pass the current failing test

The tests and the production code are written together, with the tests just a few seconds ahead of the production code.

## Keeping Tests Clean

Having dirty tests is equivalent to, if not worse than, having no tests. The problem is that tests must change as the production code evolves. The dirtie the tests, the harder they are to change.

The moral of the story is simple: Test code is just as important as production code. It is not a second-class citizen. it required thought, design, and care. It must be kept as clean as production code.

## Clean Tests

What makes a clean test? Three things. Readability, readability, and readability. Radibility is perhaps even more important in unit tests than it is in production code. 
What makes a tests readable? The same thing that makes all code readable: *clearity, simplicity, and density of expression*. In a test you want to say a lot with as few expressions as possible

## Domain-Specific Testing Language

We should build up a set of functions and utilities that make use of those APIs and that make the tests more convenient to write and easier to read. **This testing API is not designed up front; rather it eveloves from the continued refactoring of test code that has gotten too tainted by obfuscating detail.**

## A Dual Standard
The code within the testing API does have a different set of engineering standards than production code.It must still be simple, succinct, and expressive, but it need not be as efficient as production code. After all, it runs in a test envirnonment, not a production envirnoment, and those two envirnoment have very different needs.

## One Assert per Test

There is a school of thought that says that every test function should just have one assert. That's has its advandages e.g. the test is quick and easy to understand. But the main disandvandage is that you will need to duplicate lots of code.

*You should use this as guidaline, minimize number of asserts in a test function*

## Single Concept per Test

Perhaps a better rule is that we want to test a single concept in each test function.

## F.I.R.S.T

**Fast**: quick so they can run frequently.

**Independed**

**Repeatable**: they should run in any envirnoment, in your local, qa env, prod env etc.

**Self-Validating**: the tests should have a boolean output. Either theyh pass or fail. You should not have to read trhough a log file to tell whether the test pass.

**Timely**: Tests should be written before for different reason. Mainly because you may not design the production code to be testable if you write your unit tests later.

