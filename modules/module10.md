---
layout: default
permalink: module/10
---

# Module 10: Templates in C++

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/7rFKKCjL](https://classroom.github.com/a/7rFKKCjL)


## Exercise 1: Template Function
In this exercise, you will create a function template in C++ that calculates the sum of elements in an array. The function should be able to handle arrays of any data type that supports addition and initialization to zero.

1. __Setup the environment__: Review the code in the exercise1 directory in the module10 GitHub repository. 
2. __Create a function template__: In the file `exercise1.cpp` modify the `arraySum` function to be a template function that can sum generic types instead of only `int`.
3. __Update the main function__: Modify the main function to have multiple calls to the `arraySum` function with different types, such as `double`, `float`, `long`.
4. __Compile and test__: Compile and run `exercise1.cpp` to test your new template function.


## Exercise 2: Template Class

In this exercise, you will create a generic stack data structure using C++ __templates__. The stack should be able to store elements of __any__ data type and provide basic stack operations.

Steps:

1. __Setting Up the Environment__: Add your code to the exercise2 directory in the module10 GitHub repository. 
2. __Creating the Stack Header File__: Create a new file named `StackTemplate.h.` Define a class template named `StackTemplate`. Inside the class, declare a `private` member variable that will hold the stack elements. Use `std::vector<T>` as the underlying container. Use the following template declaration:
    ```c++
    template <typename T>
    class StackTemplate 
    {
    public:
        // Class definition goes here
    private:
        std::vector<T> elements;
    };
    ```
3. __Adding Basic Methods__: Add the following public methods to the `StackTemplate` class:
    * `bool isEmpty();` - To check if the stack is empty.
    * `void push(T element);` - To add an element to the top of the stack.
    * `T pop();` - To remove and return the top element of the stack. Throw `out_of_range` exception if stack is empty. 
    * `T top();` - To get the top element without removing it. Throw `out_of_range` exception if stack is empty.
4. __Implementing the Stack Methods__: Create a new file named StackTemplate.cpp. Implement each method you declared in the StackTemplate class. For example:
    ```c++
    template <typename T>
    bool StackTemplate<T>::isEmpty()  
    {
        return elements.empty();
    }

    template <typename T>
    void StackTemplate<T>::push(T element) 
    {
        elements.push_back(element);
    }
    // Continue implementing the rest of the methods...
    ```
5. __Include the Implementation__: At the end of the `StackTemplate.h` file, include the implementation file `StackTemplate.cpp`.
6. __Testing Your Stack__: Create a `main.cpp` file. Include the `StackTemplate.h` file. In the main function, create a `StackTemplate<int>` instance and test the stack operations. For example:
    ```c++
    int main() 
    {
        StackTemplate<int> intStack;
        intStack.push(10);
        intStack.push(20);
        // Test other methods and print results
        return 0;
    }
    ```
7. __Add try/catch block__: Implement exception handling for situations like popping from an empty stack.
8. __Other data types__: Create stacks with other data types (e.g., `StackTemplate<std::string>`).
9. __Add a method__: to return the size of the stack.
10. __Create a Makefile__: Define your targets and dependencies:
    * all: This target will build your entire project.
    * clean: This target will clean up the object files and the executable.
    * main.o: Target for compiling the `main.cpp` file.
    * main: Target for compiling the `main.cpp` and `StackTemplate.cpp`.
11. __Test your program__: Use your make file to compile.  Then run your program to test. 
