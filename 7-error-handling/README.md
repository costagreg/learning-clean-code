# Error Handling
Error handling is important, but if it obscures logic, it's wrong.

## Use Exception Rather Than Return Codes
Exception helps with separation of concern.

Not using exception can be messy and in the past it was possible with error code. Caller had to check for these error and handle them.

## Write Your Try-Catch-Finally Statement First.
it is good practice to start with a try-catch-finally statement when you are writing code that could throw exceptions. This helps you define what the user of that code should expect, no matter what goes wrong with the code that is executed in the try.

## Use Uncked Exception

## Provide Context with Exception

Each exception that you throw should provide enough context to determine the source and location of an error. Create informative error messages and pass them along with your exceptions. Mention the operation that failed and the type of failure.

## Provide Exception Classes in Terms of a Caller's Needs.

Consider creating an API wrapper if you want to handle exception in a different way. When you wrap a third-party API, you minimize your dependencies upon i: You can choose to move to a different library without too much penaliy.

## Don't Return Null
When we return null, we are essentially creating work for ourselves and foisting problems upon our callers.All it takes is one missing null check to send an application spinning out of control.

If you are tempted to return null from a metho, consider throwing an exception or returning a special object. If you are calling a null-returning method from a third-party API, consdier wrapping that method with a method that either throws an expcetion or returns a special case object.

## Don't Pass Null
We will have a runtime error if we pass null.

