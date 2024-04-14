---
layout: default
permalink: /lecture/q2
---

# Quiz 2 review 

### Objective

Review the course topics and content that will be assessed on the second quiz.

## Quiz Details
* Paper quiz
* __4 multi-part questions__, you will be asked to review code and answer questions about the code, write code, or draw something like a UML diagram.
* Total of 50 points
* 30 minutes to complete the quiz


## What to Study
   
__Text book__: [Programming Principles and Practice Using C++, 2nd Edition](https://richmond.primo.exlibrisgroup.com/permalink/01URICH_INST/191gg5k/alma9928032248406241) by Bjarne Stroustrup 

* Chapter 9 Classes, etc. 

__Lectures__:
* Slides: [Classes and OOP](lectures/09-Classes-OOP.pdf)
    - Classes
        * Class syntax
        * access specifiers (public, private, and protected)
    - Abstraction
    - Encapsulation
* Slides: [Enum, Static, Overloading](lectures/10-Class-Members.pdf) 
    - Constructors
    - Enumerations
    - Static members
    - Operator overloading
* Lecture Notes: [Scope, Friends, Destructors, Composition, and UML](lectures/11)
    - Scope
    - Friends
    - Destructors
    - Composition
    - UML Diagrams 
* Slides: [Inheritance, Polymorphism, Virtual Functions, Abstract Classes](lectures/12-Inheritance-Polymorphism.pdf)
    - Inheritance
    - Polymorphism
    - Virtual functions

    
## Practice Questions <a class="anchor" id="practice"></a>

### Access Specifiers (public, private, protected)

__Book.cpp__
```c++
class Book {
public:
    Book(std::string t) : title(t) {}

    std::string getTitle() const {
        return title;
    }

    void summarize() {
        std::cout << "This is a book titled: " << title << std::endl;
    }

protected:
    std::string title;
};

class Novel : public Book {
public:
    Novel(std::string t, std::string g) : Book(t), genre(g) {}

    void summarize() {
        std::cout << "This is a " << genre << " novel titled: " << title << std::endl;
    }

private:
    std::string genre;
};
```

Consider the C++ program __Book.cpp__ above.
* Describe the purpose of the protected access specifier in the Book class, and explain how it contrasts with the private access specifier.
* In the Novel class, which inherits from Book, can the summarize method directly access the title attribute? Provide a justification for your answer.
* If you create an object of the Novel class within the main function, can you directly access the title attribute from that object? Elaborate on your answer.


### Dynamic Memory Allocation and Deallocation

__Particle.cpp__
```c++
class Particle {
public:
    Particle(float x, float y) : posX(x), posY(y) {}

    void move(float dx, float dy) {
        posX += dx;
        posY += dy;
    }

    void printPosition() const {
        std::cout << "Position: (" << posX << ", " << posY << ")" << std::endl;
    }

private:
    float posX, posY;
};

int main() {
    Particle* p1 = new Particle(5.0, 7.5);
    p1->move(2.0, -3.0);
    p1->printPosition();

    // Some code here...

    return 0;
}
```
Consider the C++ program __Particle.cpp__ above.
* What does the `new` keyword do in the main function?
* What is returned from the expression `new Particle(5.0, 7.5)`?
* As the code stands, there's a potential issue related to dynamic memory management. Identify the issue and explain why it's problematic.
* Provide a modification to the code to fix the potential memory management issue you identified.


### Polymorphism and Virtual Functions

__Media.cpp__
```c++
class MultimediaContent {
public:
    virtual void play() {
        std::cout << "Playing generic multimedia content." << std::endl;
    }
};

class Song : public MultimediaContent {
public:
    void play() {
        std::cout << "Playing a melodious song." << std::endl;
    }
};

class Video : public MultimediaContent {
public:
    void play() {
        std::cout << "Streaming a captivating video." << std::endl;
    }
};

int main() {
    MultimediaContent* content1 = new Song();
    MultimediaContent* content2 = new Video();

    content1->play();  // ?
    content2->play();  // ?

    delete content1;
    delete content2;
    
    return 0;
}
```
Consider the C++ program __Media.cpp__ above.
* What is the significance of the `virtual` keyword in the `MultimediaContent` class regarding the `play` method?
* Given the `main` function provided, what will the output be when the program is executed?
* Describe what is meant by the term `polymorphism` in the context of the provided code.


### Implementing the constructor and methods of a class

Consider the following C++ code in the file `Calculator.h`.


```c++
#ifndef CALCULATOR_H
#define CALCULATOR_H

class Calculator {
public:
    // Constructor: Initializes the calculator with a given value.
    Calculator(double initialValue);

    // Adds a value to the current result.
    void add(double value);

    // Subtracts a value from the current result.
    void subtract(double value);

    // Multiplies the current result by a given value.
    void multiply(double value);

    // Divides the current result by a given value. If the given value is zero, do nothing.
    void divide(double value);

    // Returns the current result.
    double getResult() const;

private:
    double result;
};

#endif
```

Use the C++ code above to answer the following questions.

* Write the C++ code that you would put into the file `Calculator.cpp` to implement the constructor and methods for the `Calculator` class found in `Calculator.h`. Do your best to write code that will compile. Remember to use `#include` as needed for external libraries or the `Calculator.h` file.

* Draw a __UML__ diagram that represents the `Calculator` class. Remember to include the name of the class, the member variables (attributes) and their type, and member functions (methods) and their return and parameter types. You should include the access specifiers for each attribute and method. If an attribute or method is `public` indicate this with a `+` sign. If an attribute or method is `private` indicate this with a `-` sign. 