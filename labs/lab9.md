---
layout: default
permalink: lab/9
---

# Lab 9: Templates in C++

## Instructions
* First read this page then start working on lab with the GitHub classroom link below.

* Use the code in the GitHub repository for this lab.

* Github Classroom Link: [https://classroom.github.com/a/QNslZBCW](https://classroom.github.com/a/QNslZBCW)

## Objective
Develop an understanding of __C++ templates__, focusing on their application for code reusability and flexibility.


## Exercise 1: Swap Function Template

Create a generic swap function using C++ templates that can interchange the values of two variables of any data type.

Put your code for this exercise in the `swap.cpp` file in the `Exercise1` folder in your GitHub repository.

1. Create a function template called `swapValues` that can interchange the values of two variables of any data type.
2. The function should be able to handle different data types (e.g., int, float, double) for the the values to be swapped.
3. Update the `main` function in `swap.cpp` to demonstrate the usage of the `swapValues` function for different data types.
4. In the `README.md` file in your GitHub repository. Write a few sentences describing how you used a C++ template to create a generic `swapValues` function.


## Exercise 2: Area Function Templates

Create function templates to calculate the area of different geometric shapes.

Put your code for this exercise in the `area.cpp` file in the `Exercise2` folder in your GitHub repository.

1. Create three function templates that can calculate the area of different geometric shapes : `calculateAreaSquare`, `calculateAreaRectangle`, and `calculateAreaCircle`.
2. The function should be able to handle different data types (e.g., int, float, double) for the dimensions of the shapes.
3. Update the `main` function in `area.cpp` to demonstrate the usage of the calculateArea functions for different shapes and data types.
4. In the `README.md` file in your GitHub repository. Write a few sentences describing how you used a C++ template to create generic calculateArea functions.

## Exercise 3: Vector Class Template

Implement a generic vector class in C++ using templates, providing a simplified version of the functionality offered by std::vector.

Put your code for this exercise in the `Exercise3` folder in your GitHub repository.

1. Write a template class GenericVector with a template parameter for the element type. 
2. Put this implementation into the files `GenericVector.h` and `GenericVector.cpp`
3. Use the non-generic versions `IntVector.h` and `IntVector.cpp` files to help guide your coding.
4. Update the `main` function in `main.cpp` to demonstrate the usage of `GenericVector` for different data types. Don't forget to add `GenericVector.h` to `main.cpp`.
5. Modify the `Makefile` so that `GenericVector.h` and `GenericVector.cpp` are included when building the `main` target.
6. In the `README.md` file in your GitHub repository. Write a few sentences describing how you used a C++ template to create generic vector class declaration and implementation.


