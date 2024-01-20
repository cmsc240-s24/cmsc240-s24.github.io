---
layout: default
permalink: module/2
---

# Module 2: Functions, Strings, and Command Line Arguments

* First read this page then start coding module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/0iIUIHL8](https://classroom.github.com/a/0iIUIHL8)


## Exercise 1: <a class="anchor" id="exercise_1"></a>
### Palindrome Checking

The code for this exercise is in the `exercise1` directory in the module2 repository. Read the description below, and then enter your code in the palindrome.cpp file where it says 
```c++
// TODO: Write your code here.
```

<div class="requirement">
When you finish and test your code, write in the README.md file how your code works, and explain how the input is recieved from the command line via `argc` and `argv[]`.
</div>

Complete a small program to check if the input provided by the user is a palindrome. A palindrome is a string that is the same forward and backwards.

There are two main ways for testing if a string is a palindrome:

-   Iterate from forward to back, and from back to forward, and check that they are the same.

-   Create a copy of the string, in reverse, and check that the copy matches the original.

You will implement both. The main portion of the program, provided to you, looks like this:

```c

// The main function, were the program begins.
int main(int argc, char* argv[])
{
    // If the argument count does not equal 2,
    // then print a usage message.
    if (argc != 2)
    {
        cerr << "Usage: " << argv[0]
             << " <string-to-check>" << endl;
        exit(1);
    }

    // Create a new string named inputString.
    string inputString = argv[1];

    // Call check1 function.
    if (check1(inputString))
    {
        cout << inputString << " is a palindrome according to check 1" << endl;
    }
    else
    {
        cout << inputString << " is NOT a palindrome according to check 1" << endl;
    }

    // Call check2 function.
    if(check2(inputString))
    {
        cout << inputString << " is a palindrome according to check 2" << endl;
    }
    else
    {
        cout << inputString << " is NOT a palindrome according to check 2" << endl;
    }

    return 0;
}

```


<div class="requirement">

-   Complete the `palindrome` program using two checks.

-   `check1()` and `check2()` must use two distinct algorithms:
    -   `check1()` use two iterators, one from the start and one from the end of the string, to check if the front and back are the same
    -   `check2()` copy the string to a new string, in reverse, and compare the two strings using `.compare()` or `==`



Here is some sample output:

```Shell
$ ./palindrome racecar
racecar is a palindrome according to check 1
racecar is a palindrome according to check 2

$ ./palindrome madamimadam
madamimadam is a palindrome according to check 1
madamimadam is a palindrome according to check 2

$ ./palindrome amanaplanacanalpanama
amanaplanacanalpanama is a palindrome according to check 1
amanaplanacanalpanama is a palindrome according to check 2

$ ./palindrome notapalindrome       
notapalindrome is NOT a palindrome according to check 1
notapalindrome is NOT a palindrome according to check 2

$ ./palindrome               
Usage: ./palindrome <string-to-check>
```
    

</div>

---


## Exercise 2: <a class="anchor" id="exercise_2"></a>


### Compiling Multiple Files

To compile the code in the `exercise2` directory with `g++` the GNU C++ compiler using the following command:

```Shell
g++ main.cpp one.cpp two.cpp -o program
```

<div class="requirement">

In the module2 README.md file, explain how the `main()` function in main.cpp has access to the functions `printEven()` and `printOdd()`.  Explain both where the function declarations are stored, and the steps the compiler is taking to build the `program` executable. 

</div> 

---