---
layout: default
permalink: module/5
---

# Module 5: Classes - Enum, Static Members, Operator Overloading

* First read this page then start coding module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/Fgqlqkg3](https://classroom.github.com/a/Fgqlqkg3)


## Class implementation:

Start with the `class` that you wrote in [module 4](module/4). Add all of the code from module 4 to this module 5 GitHub repository. Then edit the c++ code to complete the following exercises.

### Exercise 1 - Enumeration (`enum`)
* An `enum` is a very simple user-defined type
* Use them when you want a set of values as symbolic constants

__1.__ Add an `enum` to your class code to enumerate a set of values where appropriate.
__2.__ Explain your design decision.


### Exercise 2 - `Static` member variable
* `Static` member variables can be accessed on the class itself, without creating an instance of the class
* Exists only once, regardless of how many instances of the class are created
* Shared among all instances of the class
* Value is set outside the class, typically in a source (.cpp) file

__1.__ Add a `static` member to your class code.
__2.__ Explain your design decision.

### Exercise 3 - `Static` member functions
* `Static` member functions can be called on the class itself, without creating an instance of the class
* It can only access `static` member variables or other `static` member functions directly
* It's often used as a utility function or to interact with `static` member variables.

__1.__ Add `static` member function to your class code to interact with your `static` member variable.
__2.__ Explain your design decision.

### Exercise 4 - Operator overloading
* Operator overloading is a feature in C++ that allows you to redefine the behavior of built-in operators (like `+`, `-`, `*`, etc.) for user-defined types like classes
* This enables you to use these operators in intuitive ways with objects of your custom types, making your code more readable and expressive

__1.__ Overload an operator in your class code where appropriate.
__2.__ Explain your design decision.

**Note**: Your code should compile and be well documented with code comments. But it does not have to be completely implemented such that everything operates fully.  In other words, some methods may be "stubbed" out to only print out (`cout`) "in method X".  This is an exercise to get comfortable with the C++ `class` syntax. 

---
