---
layout: default
permalink: module/7
---

# Module 7: Build Automation with Make

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/XGPs_SzF](https://classroom.github.com/a/XGPs_SzF)

## Compilation

When you compile a C++ program, the compiler often does the following steps:

1. __Preprocessing__: Handles macros, `#include` directives, and other preprocessor commands.
2. __Compilation__: Translates C++ code into assembly language. This is where a `.s` file can be generated if desired.
3. __Assembly__: Converts the assembly code into machine code, producing an object file (usually with a `.o` or `.obj` extension).
4. __Linking__: Combines multiple object files and resolves references to produce the final executable or shared library.

![CompilationPipeline](../images/CompilationPipeline.png "Compilation Pipeline")

## Exercise 1

Go to the `exercise1` directory of your module 8 GitHub repository. Put your answers to the questions below in the README.md in your module 8 GitHub repository. 

1. Run the following commands to inspect the file type of each file.
```
$ file calculate.cpp
$ file functions.cpp
$ file functions.h
```
2. Read the contents of the `calculate.cpp`, `functions.cpp`, and `functions.h` file. 
3. What is the purpose of including the `functions.h` file in `calculate.cpp`?
4. Run the following commands to run the __preprocessing__ step.
```
$ g++ -E -P calculate.cpp > calculate.i
$ g++ -E -P functions.cpp > functions.i
```
5. Read the contents of `calculate.i` and `functions.i`.
6. What has changed compared to the `.cpp` versions of these files?
7. Now run the following commands to run the __compilation__ step.
```
$ g++ -S calculate.i
$ g++ -S functions.i
```
8. Run the following commands to inspect the file type of each file.
```
$ file calculate.s
$ file functions.s
``` 
9. Read the contents of `calculate.s` and `functions.s`.
10. What has changed compared to the `.i` versions of these files?
11. Now run the following commands to run the __assembly__ step.
```
$ g++ -c calculate.s
$ g++ -c functions.s
```
12. Run the following commands to inspect the file type of each file.
```
$ file calculate.o
$ file functions.o
``` 
13. Read the contents of the `calculate.o` and `functions.o` by running.
```
$ xxd -bits calculate.o
$ xxd -bits functions.o
```
14. What has changed compared to the `.s` versions of these files?
15. Now run the following command to run the __linking__ step.
```
$ g++ calculate.o functions.o -o calculate
```
16. Why did we have to provide both `.o` files at the same time when linking?
17. Run the following commands to inspect the file type of the executable.
```
$ file calculate
```  
18. How is the `calculate` executable file different from the `.o` files?
19. Run the executable.
```
$ ./calculate
```
20. In Linux (and Unix-like systems), the return value (or exit status) of the last command executed is stored in a special shell variable `?`. You can access this value using `$?`.
```
$ echo $?
```
21. Is the return value what you expected from running `calculate`?

## Build Automation Tools: Make

__Makefile__: The `make` utility reads a special file known as a makefile. 
* The makefile (or Makefile) describes the files involved in the project and the dependencies among them. 
* Each group of lines in a makefile has the following form.
```make
target: dependencies
  <Tab> commands
```
* In this context,
    - __target__ is a file to be created
    - __dependencies__ is a list of files on which the target depends
    - __commands__ is a list of commands used to (re)create the target.
* If any of the files in a dependency list is modified, make will recompile and/or relink the target. 
* Important: a `Tab` character must precede the commands — not spaces.

## Exercise 2

Go to the `exercise2` directory of your module 8 GitHub repository. Put your answers to the questions below in the README.md in your module 8 GitHub repository. 

1. Review the `Makefile` in the `exercise2` directory.
2.  Run the `make` command. Copy and paste the result of issuing the make command.
3.  Run the `make` command again. Copy and paste the result of issuing the make command.
4. Run the commands: 
```
$ touch functions.h
$ make
``` 
Copy and paste the result of issuing both commands.

5. What did the `touch` command do in this case (`man touch`)?

## Exercise 3

Go to the `exercise3` directory of your module 8 GitHub repository. Put your answers to the questions below in the README.md in your module 8 GitHub repository. 


* One way to avoid having all files be recompiled each time is to make use of object files. 
* To create an object file for the hello.cpp source file, you could issue the command `g++ -c hello.cpp` (but do not do so here). 
* The result would be a file `hello.o`. This file is not executable because no linking has taken place, only compilation — the result of using the `-c` flag.
* Create a rule in your `Makefile` for creating `hello.o` similar to the following (remember tab, not spaces!): 
```
hello.o: hello.cpp functions.h
    g++ -g -Wall -c hello.cpp
```
* Notice that the dependencies for `hello.o` are `hello.cpp` and `functions.h`. 
* The `hello.cpp` source file as a dependency should be obvious. The function.h is also a dependency because it is included in the file hello.cpp.
* Now create similar rules for creating main.o and factorial.o. (What dependencies do these two need? Make sure to modify the corresponding commands in the current Makefile as well.)

1. Run `make`. List all `.o` files created by the make command.  
2. Run `make`. Explain the result.
3. Run `make main.o`. Copy and paste the result of issuing this command.
4. Run 
```
$ make factorial.o 
$ ls -al
```  
Is there an executable present for running main?

5. Create another rule as the last rule in Makefile that will create the target `hello` based on the dependencies `hello.o`, `main.o`, and `factorial.o`. Hint: `g++ hello.o main.o factorial.o -o hello`
6. Run: 
```
$ make hello
$ ./hello
``` 
Copy and paste the output from issuing both commands.

7. Run:
```
$ rm *.o hello
$ make
$ ./hello
```
Copy and paste the output from issuing the commands.

8. Explain the previous output. 
9. Make the necessary modification to have `hello` be the default target created by `make`.
10. Run:
```
$ touch functions.h
$ make
```
Copy and paste the output from issuing the commands.

11. Explain the previous output. 
12. Run:
```
$ touch hello.cpp
$ make
```
Copy and paste the output from issuing the commands.

13. Explain the previous output.
14. Run: `rm *.o hello`
15. Could we get make to handle cleanup work like this for us? Yes — the target does not have to be a file-to-be-created. In the examples we have seen thus far, the command has been a compile command which naturally creates a file. We can issue other command-prompt commands that do not result in a created file. The typical way to have make handle the cleanup is to create a new rule at the end of your makefile. The rule should have a target called `clean` (no dependencies) with the command `/bin/rm -f *.o hello`. Add this rule to the end `Makefile`.
16. Run: 
```
$ make
$ make clean
```
17. Copy and paste the output from issuing the commands.
18. Should the `clean` target be first in the makefile? Explain.
