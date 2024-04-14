---
layout: default
permalink: /lecture/q4
---

# Quiz 4 review 

### Objective

Review the course topics and content that will be assessed on the forth quiz.

## Quiz Details
* Paper quiz
* __5 multi-part questions__, you will be asked to review code and answer questions about the code, write code, or draw a Git graph.
* Total of 50 points
* 30 minutes to complete the quiz

## What to Study
   
__Lectures__:
* Slides: [Smart Pointers](lectures/22-Smart-Pointers.pdf) 
    - Unique Smart Pointer
    - Shared Smart Pointer
* Slides: [Build Pipelines](lectures/23-Build-Pipelines.pdf) 
    - Generating documents
    - Static Analysis
    - Unit Testing
* Lecture Notes: [Unit Testing](notes/UnitTesting.md)
    - Test First Development
    - Code Coverage
    - Writing Test Cases
* Lab 10: [Lab 10 Git and GitHub](https://cmsc240-s24.github.io/lab/10)
    - Git and GitHub
    - Drawing Git trees
* 

## Practice Questions <a class="anchor" id="practice"></a>

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




### Object-oriented programming

What are the __four__ most important concepts in object-oriented programming?  Describe them in detail. 
    
* __A__ bstraction: Abstraction means hiding the complex reality while exposing only the necessary parts. It is a way of creating a simple model of a more complex underlying entity that represents its key aspects in a way that is easy to work with for our specific purposes. This is achieved in OOP through the use of classes that showcase only relevant attributes and behaviors of objects.

* __P__ olymorphism: Polymorphism allows objects of different classes to be treated as objects of a common super class. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. It allows a single interface to represent different underlying types (data types), and a method to perform different functions based on the object it is operating on.

* __I__ nheritance: Inheritance is a mechanism that allows a new class to inherit properties and methods of an existing class. This concept facilitates code reusability, helps to establish a hierarchy in class structures, and enables the creation of more complex abstractions by building upon simpler base components.    

* __E__ ncapsulation: Encapsulation is about bundling the data (variables) and methods that operate on the data into a single unit or class. It also involves restricting direct access to some of an object's components, which is a means of preventing accidental interference and misuse of the methods and data. This is typically done using access modifiers, like `private`, `protected`, and `public` in C++.

