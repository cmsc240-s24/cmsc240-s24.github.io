---
layout: default
permalink: lab/4
---

# Lab 4: Debugging and Exception Handling

### Instructions
* First read this page then start working on lab with the GitHub classroom link below.

* Put your code in the GitHub repository for this lab.

* After you complete the lab, answer the questions in the README.md file. Enter your answers directly in the README.md file.

* Github Classroom Link: [https://classroom.github.com/a/oNrteK3G](https://classroom.github.com/a/oNrteK3G)


### Objective
Familiarize yourself with the essential features of the VSCode Debugger while working with a C++ programs. Learn and gain experience with errors and employ `try`/`catch` for exception handling.

### Part 1 - Debugging 
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
    - In the `applyDiscount` function step over each line until you reach the `return discount` line.
    - In the `applyDiscount` function, under the VARIABLES section of the debugger, change the value of discount to `20`.
    - After making this change, press "Step Out" to move back to the `processOrder` function and observe how the change impacts the total cost.
* __Completing Execution__:
    - Press "Continue" to complete the program.
    - Expected Output with discount set to 10:
    ```
    Total Cost for John Doe: $50.99
    ```
    - Expected Output with discount set to 20:
    ```
    Total Cost for John Doe: $45.99
    ```

### Part 2 - More Debugging

* __Setup__:
    - Open the file `factorial.cpp` in the `Part2` directory in the repository.
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

 
### Part 3 - Exception Handling 

Your task is to enhance the `factorial.cpp` program in the `Part3` directory to handle potential errors gracefully. Here are the steps:

* __Check for Negative Inputs__: The factorial function is only defined for non-negative integers. Modify the factorial function to check if the input number n is negative. If it is, throw an appropriate exception.

* __Handle Potential Overflow__: The result of the factorial calculation can grow rapidly for even relatively small input values. Before each multiplication, check if the next multiplication would cause an overflow. If an overflow is detected, throw an appropriate exception. __Hint__: You might find numeric_limits<unsigned long long>::max() useful for this check.

```c++
if (result > numeric_limits<unsigned long long>::max() / i) 
{
    throw overflow_error("Result will overflow.");
}
```

* __Catch Exceptions in the `main` Function__: In the `main` function, use a __try-catch__ block to catch any exceptions thrown from the factorial function. Display an appropriate error message to the user if an exception is caught.

* __Test Your Program__: Run your program and test it with various input values, including negative numbers and numbers that might cause an overflow, to ensure that your error handling works as expected.

* __Remember__: Proper error handling is essential for building robust and user-friendly software. Take this opportunity to practice identifying potential errors in code and handling them gracefully!


<div class="requirement">
After you complete the lab, answer the questions in the README.md file. Enter your answers directly in the README.md file.
</div>



