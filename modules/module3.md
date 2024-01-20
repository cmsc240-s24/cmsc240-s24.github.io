---
layout: default
permalink: module/3
---

# Module 3: Arrays, Vectors, and File I/O

* First read this page then start coding module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/X5dNm4FL](https://classroom.github.com/a/X5dNm4FL)


## Exercise 1: <a class="anchor" id="exercise_1"></a>
### Letter Counting

The code for this exercise is in the `exercise1` directory in the module3 repository. Read the description below, and then enter your code in the lettercount.cpp file where it says 
```c++
// TODO: Write your code here.
```

<div class="requirement">
When you finish and test your code, write in the README.md file how your code works.
</div>

Complete a small program to count the letters in a file. You will write a LetterCount function that takes a filename and prints to the console the number of times each letter of alphabet appears in that file. The LetterCount function should create a `vector` to store the 26 numbers to be printed. The idea being that you could store the count for all of the `a` characters in index `0` of the vector, and the count for all of the `b` characters in index `1` of the vector, etc. For example, if the file is:

```text
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

then the LetterCount function will output the following:

```text
a: 29
b: 3
c: 16
d: 19
e: 38
f: 3
g: 3
h: 1
i: 42
j: 0
k: 0
l: 22
m: 17
n: 24
o: 29
p: 11
q: 5
r: 22
s: 18
t: 32
u: 29
v: 3
w: 0
x: 3
y: 0
z: 0
```

Count all letters regardless of case (so 'Ee' is two 'e').  You can use the `tolower(char)` function from the [string](https://en.cppreference.com/w/cpp/string/byte/tolower) library if needed to convert upper case characters to lowercase. Ignore all non-alphabetic characters. You can use the `isalpha(char)` function from the [string](https://en.cppreference.com/w/cpp/string/byte/isalpha) if needed to check if a character is a letter. The textfile ipsum.txt is provided for testing your code.  


Here is some sample output:

```Shell
$ ./lettercount
Usage: lettercount <filename>

$ ./lettercount filedoesnotexist
Unable to open file: filedoesnotexist

$ ./lettercount ipsum.txt
a: 29
b: 3
c: 16
d: 19
e: 38
f: 3
g: 3
h: 1
i: 42
j: 0
k: 0
l: 22
m: 17
n: 24
o: 29
p: 11
q: 5
r: 22
s: 18
t: 32
u: 29
v: 3
w: 0
x: 3
y: 0
z: 0


```

<div class="requirement">

Complete the `lettercount` program.  You must read from the command line arguments to obtain a filename from the user.  You must open the file, read it, then keep the count of the letters in a `vector` collection.  Then iterate through that collection to print the letter counts to `cout`, the standard output character stream (terminal window), see sample output above. 

Your program should contain a `main` function that will take a filename as a command line argument, it should print a usage message if the filename is not present in the list of command line arguments, see sample output above. You should write a lettercount function with the following function prototype declaration `void lettercount(string filename);`. In this function you will open the file, read each character, and keep a count.  If the filename does not exist, print out an error message to `cerr`, the character error stream, see sample output above.
    
</div>


#### A few hints (spoilers ahead)

One way to approach this would be to build a large [switch](https://en.cppreference.com/w/cpp/language/switch) statement that has 26 `case` statements, one for each letter of the alphabet.

A more refined approach would be to refer to the [ASCII table](https://simple.wikipedia.org/wiki/File:ASCII-Table-wide.svg) of character values. Take note that lowercase `a` is the decimal 97.  You could convert the characters to lower case, then convert them to integer values.  You could subtract 97 from each integer value. This would cause the letter `a` to begin at index `0`, which could be used to index into the `vector` for storing a count. 

---


