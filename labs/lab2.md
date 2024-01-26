---
layout: default
permalink: lab/2
---

# Lab 2: File I/O

* First read this page then start coding the lab with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/1979WMkg](https://classroom.github.com/a/1979WMkg)


## Personal Diary Management System

### Objective
 Understand and practice file handling in C++ using ifstream and ofstream classes. Develop a basic Personal Diary Management System to create, read, and update diary entries.


### Problem Statement

Design a command-line interface (CLI) Personal Diary Management System that has the following features:

- Add an Entry: Each diary entry consists of a date and associated text. The entry is saved to a file with the name format YYYY_MM_DD.txt 
(e.g., 2023_09_07.txt for 7th September 2023).

- Read an Entry: Users can input a date. The system should display the diary entry for the given date if it exists or display a message stating that the entry doesn't exist.

- Update an Entry: Users can input a date and the new text they'd like to save. If an entry for the date exists, append to it. If not, create a new entry.


### Instructions:

Use the `fstream` header. Use `ifstream` to read from files and `ofstream` to write to files. Create appropriate error handling for file operations, such as when a file doesn't exist or there's an error during reading/writing. Keep the user interface simple, text-based, and intuitive.

The code for this exercise is in the lab2 repository. Read the description below, and then enter your code in the `diary.cpp` file where it says: 
```c++
// TODO: Write your code here.
```

To **append** to a file. You can open the file with the `ofstream::app` option, like this:

```c++
    ofstream diaryEntryFileStream;
    diaryEntryFileStream.open(filename, ofstream::app);
```

<div class="requirement">
When you finish and test your code, write in the README.md file how your code works. 
</div>

Here is some sample output:

```Shell
$ ./diary
Welcome to the Personal Diary Management System 1.0

Choose an operation:
(x) : Exit
(n) : Create a New Entry
(r) : Read an Entry
(a) : Append to an Entry
n
Please enter the diary entry date in the format YYYY_MM_DD: 2023_09_08
Type your diary text for 2023_09_08 (Enter END on a new line when done.):
Dear Diary,
Today I wrote a diary entry program.
END

Choose an operation:
(x) : Exit
(n) : Create a New Entry
(r) : Read an Entry
(a) : Append to an Entry
a
Please enter the diary entry date in the format YYYY_MM_DD: 2023_09_08
Type your diary text for 2023_09_08 (Enter END on a new line when done.):
The program worked!
END

Choose an operation:
(x) : Exit
(n) : Create a New Entry
(r) : Read an Entry
(a) : Append to an Entry
r
Please enter the diary entry date in the format YYYY_MM_DD: 2023_09_08

Dear Diary,
Today I wrote a diary entry program.

The program worked!

Choose an operation:
(x) : Exit
(n) : Create a New Entry
(r) : Read an Entry
(a) : Append to an Entry
r
Please enter the diary entry date in the format YYYY_MM_DD: 2025_01_01
Could not find diary entry for 2025_01_01

Choose an operation:
(x) : Exit
(n) : Create a New Entry
(r) : Read an Entry
(a) : Append to an Entry
x
```
    

---