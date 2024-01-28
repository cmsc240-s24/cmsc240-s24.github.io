---
layout: default
permalink: lab/3
---

# Lab 3: Pointers and References in C++

### Instructions
* In this lab you will work in **teams of two**, though each of you needs to commit and push to **your own individual GitHub repository**. There may be one group of size three. You will use the technique of **pair programming**, see description at the bottom of this page.

* Write the names of each team member at the top of your README.md file in your individual repositories. 

* First read this page then start coding the lab with the GitHub classroom link below.

* Put the answers to the questions below in the README.md file in the GitHub repository for this lab.

* Github Classroom Link: [https://classroom.github.com/a/wUsp_5Dr](https://classroom.github.com/a/wUsp_5Dr)




### Objective
Understand and practice file handling in C++ using pointers, dynamic memory allocation, references, and structs.


## Exercise 1

Open `ProgramOne.cpp` in an editor and inspect the source code. This program has a `changeValue` function which uses **pass-by-value** parameters.

**Now compile and run the program.**

**1.** What changes do you notice in the before and after versions of the UR id and name? 

**2.** Why? 

Keeping the original function intact, write a new but similar `changeValue` function with a different signature using pointers as the parameters (don’t forget your function prototype, if appropriate):

`void changeValue(int* someInt, string* someString);`

In the definition of the function, make sure that you dereference (with the `*` "contents of" operator) the parameters when doing the assignment (and continue to assign a different netid and name). 

Back in `main`, in addition to the existing function call, include a call to this new function (think carefully about what you need to pass in for arguments) and subsequent `cout`. 

**Recompile and run.**

**3.** What changes do you notice in the before and after versions as a result of calling your new function?

**4.** Why? 

Now, change the original **pass-by-value** version of the `changeValue` function to use reference parameters:

`void changeValue(int& someInt, string& someString);`


**NOTE**: When you use reference parameters, C++ handles **pass-by-reference** for you automatically. In other words, in the body of your function, you treat the parameters as regular variables (not as pointers, i.e., don’t dereference within your function), and C++ takes care of the **pass-by-reference**. Similarly, when you call your function, pass a variable directly — not using the variable’s address.

From the C++ Super-FAQ: [https://isocpp.org/wiki/faq/references#overview-refs](https://isocpp.org/wiki/faq/references#overview-refs)

**Important note**: Even though a reference is often implemented using an address in the underlying assembly language, please do not think of a reference as a funny looking pointer to an object. A reference **is** the object, just with another name. It is neither a pointer to the object, nor a copy of the object. It **is** the object. There is no C++ syntax that lets you operate on the reference itself separate from the object to which it refers.

In the definition of the function, make sure that you do not dereference the parameters when doing the assignment. Note that back in `main`, you already have a call to this new function (it does not explicitly pass addresses for arguments) and subsequent `cout`. 

**Compile and run the program again**, and you should notice that the reference parameters cause the before and after values to change.

**5.** What code changes are required when using a pointer as a parameter?

**6.** What code changes are required when using a C++ reference as a parameter?

**7.** What is the primary difference (in terms of effect) between **pass-by-value** and **pass-by-reference**?


## Exercise 2

Open `ProgramTwo.cpp` in an editor and inspect the source code. Note that the function named `changeValue` uses a pointer-type parameter, declares and assigns one local variable, and executes two other assignments on the parameter. 

**Compile and run the program.**

**8.** What changes do you notice in the before and after versions of `anInt` and `intPtr`?

**9.** For `anInt`, why?  

**10.** For `intPtr`, why? 


## Exercise 3

Open `ProgramThree.cpp` in an editor and inspect the source code. This program makes use of a `struct` to define a student data type, encapsulating a student’s UR ID, name, and netid. 

**11.** What is the best explanation of the apparent intent of the program as given (even if not successful in that intent)?

**12.** Compile and run the program. Does the program accomplish that intent? Why or why not?

Modify this program so that it has two functions both named `changeID`: one which uses a pointer parameter and one which uses a reference parameter.

**NOTE**: Remember that when using a `struct` variable, you use a dot `.` to access a field in the struct, but when using a `struct` pointer, you use an arrow operator `->` to access a field.

Modify `main` so that your program calls both of these functions and exhibits **pass-by-reference** functionality (you will need to use `cout` statements to convince me of the effect).

**13.** What is the best explanation of dot versus arrow use?




## Grading Rubric

### Total Points: 100

- Functionality (30 points)
   - Correctness (20 points)
      - Code produces expected output: ___/10
      - Code handles edge cases appropriately: ___/10
   - Efficiency (5 points)
      - Code runs within expected time limits: ___/5
   - Error Handling (5 points)
      - Code gracefully handles unexpected inputs or scenarios without crashing: ___/5
- Completeness (40 points)
   - All required functionality is implemented: ___/20
   - Answered lab questions in the README.md: ___/20
- Code Quality (30 points)
    - Readability (10 points)
        - Code has meaningful variable and function names: ___/5
        - Code is consistently formatted and indented: ___/5
    - Modularity (10 points)
        - Code is appropriately divided into functions: ___/5
        - Each function has a single responsibility: ___/5
    - Documentation (10 points)
        - Code includes a header comment explaining the program's purpose: ___/3
        - Each function has a comment explaining its purpose, inputs, and outputs: ___/5
        - Inline comments explain non-obvious sections of the code: ___/2


## Pair programming

Pair programming is a software development technique in which two programmers work together at one computer. One, the **driver**, writes code while the other, the **navigator**, reviews each line of code as it is typed in. **The two programmers switch roles frequently.**

