---
layout: default
permalink: module/14
---

# Module 14: C++ Smart Pointers

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/7-43ok6N](https://classroom.github.com/a/7-43ok6N)


## Exercise 1: Basic Usage of `unique_ptr`

Understand the basic mechanics of `unique_ptr` and how it manages the lifecycle of a heap-allocated object.


1. In the `exercise1` folder of your GitHub repository edit the file `main.cpp` and create a `unique_ptr` to manage a dynamically allocated object of a simple class `Box`. The Box class has one integer member variable and a constructor that sets it.
2. Implement the `printBoxValue` a function that takes a `unique_ptr<Box>` by value and prints the value of the `Box`'s member variable.
3. Demonstrate what happens when you try to copy the `unique_ptr`.
4. In the `README.md` file, explain why it is not allowed. 


## Exercise 2: Transfer of Ownership with `unique_ptr`

Learn how to transfer ownership of managed objects with `unique_ptr`.

1. In the `exercise2` folder of your GitHub repository edit the file `main.cpp` and create a `unique_ptr` managing a `Box` object.
2. Implement the `createBoxWithValue` function that returns a unique_ptr<Box>.
3. Implement the `transferOwnership` function to transfer ownership of the `Box` object from one `unique_ptr` to another.
4. In the `README.md` file, explain how the transfer of ownership works.

## Exercise 3: Introduction to `shared_ptr`

Familiarize with the basics of `shared_ptr` and reference counting.

1. Create several `shared_ptr<Box>` instances that all manage the same Box object.
2. Print the reference count of these shared pointers.
    ```c++
    cout << "Reference count: " << sharedSmartPointer.use_count() << endl;
    ```
3. Demonstrate how the reference count changes as `shared_ptr` instances are created and destroyed. 
4. In the `README.md` file, explain the different ways to create and destroy a `shared_ptr`.

## Exercise 4: Sharing and Releasing with `shared_ptr`

Learn how `shared_ptr` allows multiple owners and how to release ownership correctly.

1. Create a `shared_ptr<Box>` and another one that shares ownership with the first one.
2. Implement a function that takes a `shared_ptr<Box>` by value and another one by reference.
3. Demonstrate how passing by value and by reference to functions affects the reference count.
4. In the `README.md` file, explain why passing by value and by reference to functions affects the reference count differently.
5. Use `.reset()` to release ownership and observe how the object is only destroyed when the last `shared_ptr` is gone.

