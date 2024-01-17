---
layout: default
permalink: module/1
---

# Module 1: Introduction

* First read this page then start coding module and answering the exercise questions with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/I8edy6_T](https://classroom.github.com/a/I8edy6_T)

### Objectives

The goal of this module is to compile and run your first C++ program. 

### Table of Contents

* [Hello World in C++](#hello)
* [Compiling and executing on Unix](#compile)
* [Exercise 1](#exercise_1)
* [Exercise 2](#exercise_2)

---

## Hello World in C++ <a class="anchor" id="hello"></a>

Here is the classic Hello World program in C++:

 ```C++
// This program outputs the message “Hello, World!”
#include <iostream>
using namespace std;

int main() 
{
	cout << "Hello, World!" << endl;
	return 0;
}
 ```

The `#include` is a preprocessor directive to load the `iostream` library.

Execution starts in a function called `main`. There are other signatures for `main` that include arguments to the `main` function as we will see. The return type here is `int`, which specifies that an integer will be returned by the main function. 

The name `cout` refers to the standard output stream and along with its output operator `<<` the string "Hello, World!" is put into the character output stream and will appear on the screen.

The name `endl` is the newline character that will be also added to the character output. 

 

#### Compiling and executing on Unix <a class="anchor" id="compile"></a>

The program above is a plain text file, as in any programming language.

The file extension needs to be `.cpp`.

The file name need not be hello.

**To compile:**

```shell
g++ hello.cpp -o hello
```
    

This produces an executable called `hello` which can be executed as:

```shell
./hello
```

The compiler options (switches):

- The simplest form on invoking the g++ compiler is:

```Shell
	g++ hello.cpp 
```

- This produces an executable called a.out (by tradition). This is an abbreviated form of "assembler output".
- The `-o` option lets you specify the name of the executable.

 
# Exercise 1: <a class="anchor" id="exercise_1"></a>
* Remove the `<< endl` from `hello.cpp` but keep the `;` semicolon at the end of the line and see what happens. Recompile and run. 

* Describe what happened. Put your answer in the `README.md` file in your GitHub repository.

___

<br />
<br />


# Exercise 2: <a class="anchor" id="exercise_2"></a>
* The following program should not compile. Fix it and explain why.

```C++
using namespace std;

int main() 
{
	cout << "Why oh why does this program fail to compile?!?!" << endl;
    
	return 0;
}
```

* Describe the error and explain the fix. Put your answer in the `README.md` file in your GitHub repository.

* Fix the code in `fixme.cpp`

___




  
