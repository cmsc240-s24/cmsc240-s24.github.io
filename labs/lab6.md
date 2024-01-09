---
layout: default
permalink: lab/6
---

# Lab 6: C++ Debugging Lab: Working with the VSCode Debugger

### Instructions
* First read this page then start working on lab with the GitHub classroom link below.

* Put your code in the GitHub repository for this lab.

* After you complete the lab, answer the questions in the README.md file. Enter your answers directly in the README.md file.

* Github Classroom Link: [https://classroom.github.com/a/xylMar4l](https://classroom.github.com/a/xylMar4l)


### Objective
Familiarize yourself with the essential features of the VSCode Debugger while working with a C++ programs.

### Debugging - Part 1
* __Setup__:
    - Open the file `ecommerce.cpp` in the `Part1` directory in the repository.
* __Setting Breakpoints__:
    - Set a __breakpoint__ at the start of the `main` function.
    - Set another __breakpoint__ inside the `processOrder` function.
    - Add a third __breakpoint__ in the `applyDiscount` function.
* __Start Debugging__: 
    - Launch the debugger. First click the debug icon in the activity bar on the left. Then click the "Run and Debug" button. 
* __Stepping Through the Code__:
    - When the debugger pauses at main, press "Step Over" until you get to the `processOrder` function call.
    - Now, press "Step Into" to dive into the `processOrder` function.
    - Inside the `processOrder` function, you'll soon see the `applyDiscount` function call. First, press "Step Over" to notice how you skip the internals of `applyDiscount` and directly get its return value.
    - Run the `processOrder` function again. This time, when you're at `applyDiscount`, press "Step Into" to go inside it and inspect its inner workings.
* __Observing the Call Stack__:
    - Inside the `applyDiscount` function, take a moment to observe the CALL STACK pane. You should see the function hierarchy: `applyDiscount` called from `processOrder` which was called from `main`.
* __Modifying Variables & Stepping Out__:
    - In the `applyDiscount` function, under the VARIABLES section, change the value of user to "Jane Doe".
    - After making this change, press "Step Out" to move back to the `processOrder` function and observe how the change impacts the total cost.
* __Completing Execution__:
    - Press "Continue" to complete the program.
    - Expected Output:
    ```
    Total Cost for John Doe: $50.99
    ```
    - Note: If the user was changed to "Jane Doe" during debugging, the discount wouldn't be applied, and the total cost would be $55.99.

### Debugging - Part 2

* __Setup__:
    - Open the file `Student.cpp` in the `Part2` directory in the repository.
* __Setting Breakpoints__: 
    - Set __breakpoints__ inside the `read_students_from_file` function and inside the `catch` block in the `main` function.
* __Start Debugging__: 
    - Start debugging. 
    - As the debugger stops at the __breakpoint__, inspect:
        * The state of the file object to ensure the file has been read correctly.
        * The values of the `name` and `age` variables.
        * The contents of the students vector after reading from the file.
* __Debugging with Error Handling__:
    - Intentionally introduce an error by renaming the `students.txt` file to `students_renamed.txt`.
    - Debug the program again. This time, the debugger should stop inside the `catch` block.
    - Inspect the thrown exception's message by examining the `ex` variable.
    - Fix the error by renaming the file back to `students.txt` or updating the filename in the code.
* __Enhance the `Student` class__: 
    - Add more attributes, such as `grade` or `major`. 
    - Modify the file I/O functions accordingly and use the debugger to ensure everything works as expected.
    - Introduce a few more intentional errors or exceptions and practice using the debugger to catch and understand them.


### Debugging - Part 3

* __Setup__:
    - Open the file `factorial.cpp` in the `Part3` directory in the repository.
* __Setting Breakpoints__: 
    - Set a __breakpoint__ inside the factorial function.
* __Start Debugging__: 
    - Launch the debugger.
    - As the debugger stops at the __breakpoint__:
        * Inspect Variables: Hover over the variable n to observe its value during each recursive call.
        * Step Through the Code: Use the step-over and step-into buttons to navigate through the recursive calls.
    - Try to identify the reason why the recursion never terminates.
* __Fixing the Recursive Function__:
    - Once you've identified the missing base case, modify the factorial function to include a termination condition for the recursion.
    - Debug the program again to ensure the recursive function now works correctly.
    - Expected Output:
    ```
    Factorial of 10 is: 3628800
    ```
* __Now try__: 
    - Modifying the input value (number) to larger values and see how high you can go before running into potential issues. 
    - Observe how the call stack grows with larger input values.
    - Introduce other recursive functions, like the Fibonacci sequence, and practice debugging them.

 
<div class="requirement">
After you complete the lab, answer the questions in the README.md file. Enter your answers directly in the README.md file.
</div>



