# Unit Tests

## The Three Laws of TDD

*First Law* You may not write production code until you have written a failing unit test

*Second Law* You may not write more of a unit test than is sufficient to fail, and not compiling is failing

*Third Law* You my not write more production code than is sufficient to pass the current failing test

The tests and the production code are written together, with the tests just a few seconds ahead of the production code.

## Keeping Tests Clean

Having dirty tests is equivalent to, if not worse than, having no tests. The problem is that tests must change as the production code evolves. The dirtie the tests, the harder they are to change.

The moral of the story is simple: Test code is just as important as production code. It is not a second-class citizen. it required thought, design, and care. It must be kept as clean as production code.
