---
layout: default
permalink: /lecture/27
---

# Lecture 27: Final exam review 

### Objective

Review the course topics and content that will be assessed on the final exam.

### Lecture Topics

* [Exam Details](#exam)
* [What to Study](#study)
* [Practice Questions](#practice)

## Exam Details <a class="anchor" id="exam"></a>

* Paper exam
* __10  questions__ (10 points each)
* Total of 100 points
* 3 hours to complete the exam

```
if (course_evaluation_response_rate == 100%)
{
    students_allowed_one_sheet_of_notes = true
}
```

### Links to Student Evaluation Form

__Section 2 10:30 - 11:45am__
[https://p3.courseval.net/etw/ets/et.asp?nxappid=0E2&nxmid=GetSurveyForm&wsedrq=W0PMDH7373](https://p3.courseval.net/etw/ets/et.asp?nxappid=0E2&nxmid=GetSurveyForm&wsedrq=W0PMDH7373)

__Section 1 1:30 - 2:45pm__
[https://p3.courseval.net/etw/ets/et.asp?nxappid=0E2&nxmid=GetSurveyForm&wsedrq=W0PMDH6372](https://p3.courseval.net/etw/ets/et.asp?nxappid=0E2&nxmid=GetSurveyForm&wsedrq=W0PMDH6372)


## What to Study <a class="anchor" id="study"></a>

- Makefiles
- Try/Catch
- Smart Pointers 
- Templates 
- Regular Expressions
- Unit Testing
- Git
- Inheritance
- Object-Oriented Programming

    
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



### C++ Smart pointers

Consider the following C++ code.

__main.cpp__
```c++
#include <iostream>
#include <memory>
using namespace std;

class Item 
{
public:
    Item() { cout << "Item constructed" << endl; }
    ~Item() { cout << "Item destroyed" << endl; }
};

void process(shared_ptr<Item>& sharedItem) 
{
    shared_ptr<Item> localShared = sharedItem;

    cout << "Reference count inside function = " << localShared.use_count() << endl;
}

int main() 
{
    shared_ptr<Item> myItem{new Item()};

    cout << "Reference count in main, before function call = " << myItem.use_count() << endl;

    process(myItem);

    cout << "Reference count in main, after function call = " << myItem.use_count() << endl;

    return 0;
}
```

* Is there any memory leak? Why or why not?
* What is the output of the program?
* Why is the `Item` destructor __not called__ when returning from the `process` function? 
* Why is the `Item` destructor __called__ when returning from the `main` function? 


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
    Phone Number Rules:

    For this exercise, we'll consider North American phone numbers, 
    which typically follow the format (NPA) NXX-XXXX, where:

        NPA (Numbering Plan Area) is the area code.
        NXX is the central office code, and it must not start with 0 or 1.
        XXXX is the line number.

    Add a regex pattern that will match the phone number rules above as valid.
*/

#include <iostream>
#include <regex>
#include <string>
using namespace std;

int main() 
{
    string phone;
    cout << "Enter a phone number: ";
    getline(cin, phone);

    // Define a regular expression pattern for phone number validation
    regex pattern{R"( ...REGULAR EXPRESSION HERE... )"};

    if (regex_match(phone, pattern)) 
    {
        cout << "Valid phone number!" << endl;
    } 
    else
    {
        cout << "Invalid phone number." << endl;
    }

    return 0;
}
```

* Write a __Regular Expression__ that can be used in the code above. This `regex pattern` should match the Phone Number Rules as described in the code comments. 

### Unit Testing 

Consider the following C++ code.

__test.cpp__
```c++
#define DOCTEST_CONFIG_IMPLEMENT_WITH_MAIN

#include <stdexcept>
#include <vector>
#include "doctest.h"


using namespace std;

// Function prototype
int maxElement(vector<int> nums); 

TEST_CASE("Testing the maxElement function") 
{
    CHECK(maxElement({1, 2, 3, 4, 5}) == 5);
    CHECK(maxElement({-10, -20, -30, -40, -5}) == -5);
    CHECK(maxElement({100, 200, 300, 400, 500}) == 500);
    CHECK(maxElement({42}) == 42);
    CHECK_THROWS_AS(maxElement({}), invalid_argument);
}
```

* Write the implementation of the `maxElement` function that can be used to pass the test case provided in the code above.  


### Unit Testing

Consider the following C++ code.

__test.cpp__
```c++
#define DOCTEST_CONFIG_IMPLEMENT_WITH_MAIN

#include <stdexcept>
#include "doctest.h"

using namespace std;

string numberClassifier(int number) 
{
    if (number == 0) 
    {
        throw invalid_argument("Number must not be zero");
    } 
    else if (number > 0) 
    {
        if (number % 2 == 0) 
        {
            return "Even Positive";
        } 
        else 
        {
            return "Odd Positive";
        }
    } 
    else 
    { 
        if (number % 2 == 0) 
        {
            return "Even Negative";
        } 
        else 
        {
            return "Odd Negative";
        }
    }
}
```

In the space below write a unit test that will provide __100%__ statement coverage of the `numberClassifier` function. 


### Git

Consider the following Git commands.

```bash
$ git init
$ git branch -m main
$ echo "Line One of Readme File" > README.md 
$ git add README.md
$ git commit -m "Initial Commit"
$ echo "Line Two of Readme File" >> README.md 
$ git add README.md
$ git commit -m "Second Commit"
$ git branch my_feature_branch
$ git checkout my_feature_branch
$ echo "Line Three of Readme File" >> README.md
$ git add README.md
$ git commit -m "Initial Feature Branch Commit"
$ git checkout main
$ echo "New file" > anotherfile.txt
$ git add anotherfile.txt
$ git commit -m "Third Commit"
$ git merge my_feature_branch -m "Merging Feature"
```

* __Draw__ the Git graph that would result from running all of the commands above. Include the commits on both the `main` and `feature` branches.


### Object-oriented programming: Inheritance

Consider the following C++ code.

__main.cpp__
```c++
#include <iostream>

using namespace std;

class Square 
{
public:
    Square(double s) : side(s) { }

    double getArea() 
    {
        return side * side;
    }

private:
    double side;
};


class Box : public Square 
{
public:
    Box(double s, double h) : Square(s), height(h) { }

    double getVolume()
    {
        // Base square area * height
        return getArea() * height; 
    }

private:
    double height;
};


int main() 
{
    // Example: Box with side 5 and height 10
    Box myBox(5, 10); 
    cout << "Area of the base square: " << myBox.getArea() << endl;
    cout << "Volume of the box: " << myBox.getVolume() << endl;
    return 0;
}
```

* Can a method within the `Box` class directly access the `side` variable? Why or why not?
* Why is the `side` variable `private` in the `Square` class, and how is this beneficial for object-oriented design?
* How does the `Box` class utilize the properties of the `Square` class?
* How does the `myBox` instance of the `Box` class in the `main` function have access to the `getArea()` method?


### Object-oriented programming

What are the __four__ most important concepts in object-oriented programming?  Describe them in detail. 
    
* __A__ bstraction: Abstraction means hiding the complex reality while exposing only the necessary parts. It is a way of creating a simple model of a more complex underlying entity that represents its key aspects in a way that is easy to work with for our specific purposes. This is achieved in OOP through the use of classes that showcase only relevant attributes and behaviors of objects.

* __P__ olymorphism: Polymorphism allows objects of different classes to be treated as objects of a common super class. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. It allows a single interface to represent different underlying types (data types), and a method to perform different functions based on the object it is operating on.

* __I__ nheritance: Inheritance is a mechanism that allows a new class to inherit properties and methods of an existing class. This concept facilitates code reusability, helps to establish a hierarchy in class structures, and enables the creation of more complex abstractions by building upon simpler base components.    

* __E__ ncapsulation: Encapsulation is about bundling the data (variables) and methods that operate on the data into a single unit or class. It also involves restricting direct access to some of an object's components, which is a means of preventing accidental interference and misuse of the methods and data. This is typically done using access modifiers, like `private`, `protected`, and `public` in C++.
    

