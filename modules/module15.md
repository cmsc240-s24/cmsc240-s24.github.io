---
layout: default
permalink: module/15
---

# Module 15: Build Pipelines 

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/8r3AgrHI](https://classroom.github.com/a/8r3AgrHI)

## Resources

* [doxygen documentation](https://www.doxygen.nl/manual/index.html)
* [cppcheck List of Checks](https://sourceforge.net/p/cppcheck/wiki/ListOfChecks/)
* [doctest tutorial](https://github.com/doctest/doctest/blob/ae7a13539fb71f270b87eb2e874fbac80bc8dda2/doc/markdown/tutorial.md)

## Setup
In order to view the generated documentation in HTML, install the __Live Preview__ webpage previewer for VS Code extension.

![LivePreview](../images/LivePreview.png "Live Preview")


## Exercise 1 - Document generation with doxygen: 

1. Review the code in the GitHub repository for this module. 
2. Edit the file `BankAccount.h` and add doxygen comment annotations to each method, member variable, class, and file. 
3. These comments should include all of the following annotations when needed: `@file`, `@class`, `@brief`, `@param`, `@return`, `@throw` or `@exception`.
4. Add a documentation generation target to the `Makefile`.
    ```
    docs: main.cpp BankAccount.cpp BankAccount.h
        doxygen doxyfile
    ```
5. Also add `docs` target as a dependency to the `all` target. 
6. Run the `Makefile` to build the documentation.
7. View the documentation and verify your new comments are included.


## Exercise 2 - Static Analysis with cppcheck:

1. Add a static analysis target to the `Makefile`.
    ```
    static-analysis:
        cppcheck *.cpp
    ```
2. Also add the `static-analysis` target as a dependency to the `all` target.
3. Run the `Makefile` to view the static analysis results.
4. Fix any issues in the code found during static analysis.


## Exercise 3 - Unit Testing with doctest:

1. Review the test case provided in the `BankAccountTests.cpp` file.
2. Add any tests needed to get full code coverage of the `BankAccount.cpp` file.
3. Add a target to the `Makefile` that will build the unit test program.
    ```
    BankAccountTest: BankAccountTest.cpp BankAccount.cpp BankAccount.h
        g++ BankAccountTest.cpp BankAccount.o -o BankAccountTest
    ```
4. Add a run unit tests target to the `Makefile`.
    ```
    run-unit-tests: BankAccountTest
        ./BankAccountTest
    ```
5. Also add the `run-unit-tests` target as a dependency to the `all` target.
6. Run the `Makefile` to run the unit tests and review the results.
7. Fix any issues with the code or the tests if needed.
