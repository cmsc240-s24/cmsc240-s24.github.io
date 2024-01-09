---
layout: default
permalink: /notes/UnitTesting
---

# Unit Testing in C++

### Introduction to Unit Testing
Unit Testing is a fundamental practice in modern software development, aiming to ensure that the smallest parts of an application, known as units, function independently as expected. These units are often individual functions, methods, or classes. Unit tests are written and executed by developers, often using a specialized framework designed for this purpose. 


### Why Unit Testing?
Unit Testing is essential because it helps catch bugs early in the development cycle, reducing the cost and time to fix them. It ensures that each unit of the software can be tested in isolation, thereby verifying its correctness. By writing tests, developers also create a safety net that facilitates refactoring and improves the design of the software without fear of breaking existing functionality.

- **Early Bug Detection**: Bugs are caught early in the development cycle
- **Facilitates Changes**: Safely allows changes and simplification of the code
- **Simplifies Integration**: Reduces integration issues by ensuring that each unit functions correctly before integration
- **Documentation**: Acts as documentation for the system


### Writing Test Cases
Writing test cases is a craft that involves planning and understanding the expected behavior of the code. A well-written test case not only verifies the correctness of the code but also serves as documentation for its intended functionality. Effective test cases use best practices such as the Arrange-Act-Assert (AAA) pattern.

- **Arrange-Act-Assert (AAA)**: Common pattern for organizing test code
    - Arrange: Set up the object and scenarios
    - Act: Perform the actions that lead to the result we are verifying
    - Assert: Check that the expected results have occurred
- **Test Naming**: Should be descriptive and indicate what they are testing
- **Positive and Negative Tests**: Test for both correct behavior and failure modes


### Unit Testing Frameworks in C++
A variety of frameworks are available to assist with unit testing in C++. These frameworks provide tools to easily write and run tests, as well as to check a variety of conditions through assertions. Here are some of the most popular C++ unit testing frameworks and their strengths and typical use cases.

- **doctest**: Claims to be the lightest feature-rich C++ single-header testing framework and is particularly well-suited for test-driven development
- **Google Test (gtest)**: Offers a rich set of assertions and user-friendly output, and is widely used in the industry
- **CppUTest**: It's minimalist and promotes the use of mock objects for C and C++ with a focus on simplicity
- **Catch2**: Stands out for its simple syntax and header-only deployment, making it very easy to integrate into projects
- **UnitTest++**: Designed to be a lightweight unit testing framework for C++

Each of these frameworks has its own strengths, and the choice often depends on the specific needs of the project and the preferences of the development team.  We will use **doctest** for unit testing in this course.


### Test-Driven Development (TDD)
Test-Driven Development is a software development approach where tests are written before the code that is to be tested. It emphasizes a short development cycle that includes writing a failing test, making it pass, and then refactoring the code. The TDD cycle encourages writing clean, testable, and maintainable code.

- **Red-Green-Refactor**: The cycle of TDD
    - Red: Write a failing test
    - Green: Write the minimal amount of code to make the test pass
    - Refactor: Clean up the code while keeping the tests green
- **Benefits**: More maintainable code, encourages better design


### Mocking and Stubs
When unit testing, it is often necessary to use mock objects and stubs to simulate the behavior of real objects. This is particularly important when the real objects are difficult to incorporate into a test, such as user interfaces, databases, or services. Mocking and stubbing can be used to isolate the unit of interest and to create controlled test scenarios.

- **Purpose**: To isolate the unit of code being tested
- **Mocking Frameworks**: Google Mock (part of Google Test), FakeIt, Hippomocks


### Code Coverage
Code coverage is a measure used to describe the degree to which the source code of a program is executed when a particular test suite runs. It provides a visual measurement of what source code is being covered by tests and which areas need more testing. This metric helps in identifying untested parts of a codebase, ensuring that the most critical paths are tested.

- **Types of Coverage**:
  - **Statement Coverage**: Measures if each statement in the code is executed at least once
  - **Branch Coverage**: Ensures that every possible branch from each decision point is executed
  - **Path Coverage**: Tests all the paths of execution are taken within each function
  - **Condition Coverage**: Checks that each boolean sub-expression evaluated both to true and false
- **Best Practices**: Strive for high coverage percentage but beware of the fallacy that high coverage equals well-tested code


### Best Practices
To reap the full benefits of unit testing, certain best practices should be followed. These practices not only make the tests more effective but also easier to maintain and understand. Using Best practices for unit testing can help avoid common pitfalls and improve the overall quality of the test suite.

- **Keep Tests Fast**: Slow tests can become a barrier to their usefulness
- **Test One Thing at a Time**: Each test should be focused on a single behavior
- **Readable Tests**: Should be easy to understand what is being tested and why


### Common Pitfalls
Despite its many benefits, unit testing can be challenging and there are common pitfalls that developers should be aware of. Understanding these pitfalls and knowing how to avoid them is crucial for successful unit testing. Here are some of the most common issues faced when writing unit tests, with strategies on how to overcome them.

- **Writing Tests After Bugs**: Tests should be written before bugs are known.
- **Not Running Tests Often**: Tests should be run frequently to catch regressions.
- **Ignoring Flaky Tests**: Unreliable tests should be fixed or removed.


### Conclusion
Unit testing is an indispensable part of the software development lifecycle. It's a practice that, when done correctly, leads to higher code quality, fewer bugs, and a more robust codebase.


### Resources

[DocTest tutorial](https://github.com/doctest/doctest/blob/master/doc/markdown/tutorial.md)


---
