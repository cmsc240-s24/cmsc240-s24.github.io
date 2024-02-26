---
layout: default
permalink: lab/7
---

# Lab 7: Valgrind - Memory debugging tool

### Instructions
* First read this page then start working on lab with the GitHub classroom link below.

* Use the code in the GitHub repository for this lab.

* As you work through the lab, answer the questions in the `README.md` file. Enter your answers directly in the `README.md` file.

* Github Classroom Link: [https://classroom.github.com/a/vrfQ_o7i](https://classroom.github.com/a/vrfQ_o7i)


### Objective
In this lab, you will learn to use __Valgrind__, a very handy memory debugging tool. Using Valgrind, you can find many memory management errors in your programs, include memory leaks. So why should you use Valgrind? 

“___Valgrind will save you hours of debugging time.___”

particularly when using dynamically allocated memory. When using dynamic memory management in C++, you should make frequent use of Valgrind.

Now let’s walk through some intentionally buggy example programs, demonstrating the use of Valgrind to find the bugs and highlighting common memory mistakes along the way.

### Program 1

* Open `prog1.cpp` and carefully read through the code, and locate (but do not correct) the program error. (Note: The error is not a compile-time error; it is a subtle run-time error that, in this program, won’t even show itself when you execute the program.)
* Now compile the program. Valgrind requires you to compile with a `-g` flag to turn debugging information on, e.g.,
    ```
    $ g++ -g prog1.cpp -o prog1
    ```     
* Execute the program without using Valgrind. You will see that the error doesn’t rear its ugly head (but that doesn’t mean that in bigger, more complex programs it wouldn’t!).
* Now run the program using Valgrind:
    ```
    $ valgrind ./prog1
    ```       
* Valgrind will find one error, listing the name of the program, the line on which the error occurred, and the type of error.
* Complete questions 1 and 2 in the `README.md` file.
* As another approach here, recompile the program with the `-Wall` flag (indicating that all compile warnings should be displayed), and note what happens.
* Now correct the program, recompile, and rerun using Valgrind to make sure the error is no longer present.

### Program 2
 
* Open `prog2.cpp` and try to locate (but do not correct) the error. This error, although not a compile-time error, can result in a very serious run-time error.
* Compile the program and execute without Valgrind. 
* Ugh — a _segmentation fault_. A sign of the  mismanagement of memory.
* Now run the program again using Valgrind — still a segmentation fault, but at least you have more meaningful feedback. In the Valgrind output, find all instances of `prog2.cpp` with associated line numbers.
* Complete questions 3 and 4 in the `README.md` file.
* Now correct all errors in the program, recompile, and rerun using Valgrind to make sure no errors are present.

### Program 3

* Open `prog3.cpp` and locate the error.
* Compile the program and execute without Valgrind. You should not receive a runtime error; however, an error does exist in the program.
* Try changing `intArraySize` to 10 000. Recompile and rerun. What happens?
* Change `intArraySize` to 100 000. Recompile and rerun. What happens?
* Now run the program again using Valgrind.
* Complete questions 5 and 6 in the `README.md` file.
* Now correct the program, recompile, and rerun using Valgrind to make sure no errors are present.

### Programs 4, 5

* Repeat the process with `prog4.cpp`. 
    - Make sure to complete questions 7 and 8 in the `README.md` file.
* Repeat the process with `prog5.cpp`. 
    - Make sure to complete question 9 and 10 in the `README.md` file. 

### Program 6

* The final program, `prog6.cpp`, contains a subtle error that can come back to really bite you in programs that dynamically allocate a lot of memory.
* Try to locate the error, then run using Valgrind.
* Valgrind reports no errors. We’re no longer dealing with an egregious memory error, but a more subtle one known as a memory leak. A memory leak occurs when you allocate space dynamically, and then subsequently lose any pointer to that memory (e.g., if you reassign the pointer) without having freed the memory that was associated with that pointer.
* Run the program again using Valgrind, but now turn on Valgrind’s full memory leak reporting:
    ```
    $ valgrind --leak-check=full ./prog6
    ```        
* So you see that memory is definitely being leaked somewhere. Determine where.
* Complete questions 11 and 12 in the `README.md` file.
* Now correct the program, recompile, and rerun using Valgrind to make sure that no memory leaks are present.


### Acknowledgements

This lab is based on the Valgrind lab created by Prof. Doug Szajda at UR and Prof. Will Jones at Clemson University. 