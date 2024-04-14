---
layout: default
permalink: /lecture/q3
---

# Quiz 3 review 

### Objective

Review the course topics and content that will be assessed on the third quiz.

## Quiz Details
* Paper quiz
* __5 multi-part questions__, you will be asked to review code and answer questions about the code, write code, or write something like a Makefile.
* Total of 50 points
* 30 minutes to complete the quiz

## What to Study
   
__Lectures__:
* Slides: [Errors and Exception Handling](lectures/08-Error-Handling.pdf)
    - Try/Catch blocks
    - Throwing exceptions
* Slides: [Make and Makefiles](lectures/15-Make-Makefiles.pdf)
    - Make
    - Makefiles
* Lecture Notes: [Regular Expressions in C++](lecture/16) 
    - Regex for validation
    - Regex for search
    - Regex in C++
* Slides: [Serialization in C++](lectures/17-Serialization.pdf)
    - Serialization
    - Deserialization 
* Slides: [C++ Templates](lectures/18-Templates.pdf)
    - Function templates
    - Class templates

    
## Practice Questions <a class="anchor" id="practice"></a>

### Makefiles

Consider the following C++ code.  

__main.cpp__
```c++
// main.cpp - Main function for the Library Management System

#include "Library.h"

int main() 
{
    Library library;
    library.addBook(Book("1984"));
    library.addBook(Book("Brave New World"));

    library.showBooks();
    return 0;
}
```

__Book.h__
```c++
// Book.h - Header file for the Book class

#ifndef BOOK_H
#define BOOK_H

#include <string>

class Book 
{
public:
    Book(const std::string& title);
    std::string getTitle() const;
private:
    std::string title;
};

#endif // BOOK_H
```

__Book.cpp__
```c++
// Book.cpp - Implementation of the Book class

#include "Book.h"

Book::Book(const std::string& title) : title(title) {}

std::string Book::getTitle() const 
{
    return title;
}
```

__Library.h__
```c++
// Library.h - Header file for the Library class

#ifndef LIBRARY_H
#define LIBRARY_H

#include <vector>
#include "Book.h"

class Library 
{
public:
    void addBook(const Book& book);
    void showBooks() const;
private:
    std::vector<Book> books;
};

#endif // LIBRARY_H
```

__Library.cpp__
```c++
// Library.cpp - Implementation of the Library class

#include <iostream>
#include "Library.h"

using namespace std;

void Library::addBook(const Book& book) 
{
    books.push_back(book);
}

void Library::showBooks() const 
{
    for (Book& book : books) 
    {
        cout << book.getTitle() << endl;
    }
}
```

* In the space below write a `Makefile` with the following targets: 
    * **main** - default target that builds the executable file named `main` using the object files
    * **main.o** - target that will build the `main.o` object file
    * **Book.o** - target that will build the `Book.o` object file
    * **Library.o** - target that will build the `Library.o` object file
    * **clean** - target that will remove the object files and the executable file
* What command would you run to build the executable file named `main`?
* What will happen if you run this command a second time without modifying any files?
* What will happen if you run this command again after modifying **only** `main.cpp`?


### C++ Exception handling with try/catch

Consider the following C++ code.

__main.cpp__
```c++
// Will throw an exception on bad input.
int area(int length, int width)     
{
    // Validate the inputs.
    if(length <= 0 || width <= 0)
    { 
        // Throw an invalid argument exception.
        throw invalid_argument{"Bad argument to area()"};
    }

    int result = length * width;

    // Check for an overflow in the result.
    if (result / length != width)
    {
        // Throw an overflow error exception.
        throw overflow_error{"Overflow occurred in area()"};
    }

    return result;
}


int main()
{
    int l;
    int w;
    cout << "Enter values for length and width:" << endl;
    cin >> l >> w;
    
    int result = area(l, w);
    cout << "Area == " << result << endl;

    return 0;
}
```

* What is the output of the program when the numbers `4` and `5` are entered for `l` and `w`?
* What will occur when the numbers `-4` and `0` are entered for `l` and `w`?
* Rewrite the `main` function so that the exceptions thrown from the `area` function are caught and an error message is printed to the standard output. 
* **After** your changes to the `main` function what is the output of the program when the numbers `-4` and `0` are entered for `l` and `w`?


### C++ Templates

Consider the following C++ code.

__main.cpp__
```c++
#include <iostream>
#include <vector>
using namespace std;

double averageVector(vector<double> vec) 
{
    if (vec.empty()) 
    {
        // Return 0 for empty vector
        return 0.0; 
    }

    double sum = 0.0;

    for (double num : vec) 
    {
        sum += num;
    }

    return sum / vec.size();
}

int main() 
{
    vector<double> vec = {1.5, 2.5, 3.5, 4.5, 5.5};
    cout << "Average of vector elements is " << averageVector(vec) << endl;
    return 0;
}
```

* Write a C++ template version of the `averageVector` function so that it will work with both `int` and `double` types.

### Regular Expressions

Consider the following C++ code.

__main.cpp__
```c++
/*
Vehicle Registration Number Validation:
Validate vehicle registration numbers for a specific format. 
Here are the rules for validating the vehicle registration numbers:

    The registration number must start with 2 to 3 uppercase letters.
    This is followed by a dash ('-').
    After the dash, there should be a sequence of 4 digits.
    This is followed by a dash ('-')
    After the second dash, it ends with 1 to 2 uppercase letters.

Add a regex pattern that matches the vehicle registration number validation rules above as valid.
*/

#include <iostream>
#include <regex>
#include <string>
using namespace std;

int main()
{
    string registrationNumber;
    cout << "Enter a vehicle registration number: ";
    cin >> registrationNumber;

    // Define a regular expression pattern for vehicle registration number validation
    regex pattern{R"( YOUR REGEX PATTERN HERE )"};

    if (regex_match(registrationNumber, pattern))
    {
        cout << "Valid vehicle registration number!" << endl;
    }
    else
    {
        cout << "Invalid vehicle registration number." << endl;
    }

    return 0;
}
```

* Write a __Regular Expression__ that can be used in the code above. This `regex pattern` should match the Vehicle Registration Number rules as described in the code comments. 


### Serialization 

Be able to answer the following questions:

1. What is serialization? 

2. What is deserialization? 

3. Give an example of when you would use serialization/deserialization.




