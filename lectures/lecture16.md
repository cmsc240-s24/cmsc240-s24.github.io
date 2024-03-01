---
layout: default
permalink: /lecture/16
---

# Lecture 16: Regular Expressions in C++

### Objective
Equip students with an understanding of regular expressions and their practical application in C++ programming, enabling them to proficiently utilize regular expressions for pattern matching, text manipulation, and data extraction in real-world programming scenarios.

Module 8: [https://classroom.github.com/a/zRXzMlfT](https://classroom.github.com/a/zRXzMlfT)

### Lecture Topics

* [Introduction to Regular Expressions](#introduction)
* [C++ Regular Expression Library](#library)
* [Raw Strings in C++](#raw)
* [Example: Validating an Email Address](#email)
* [Regular Expressions Tutorial](#tutorial)
* [Resources](#resources)


#### Introduction to Regular Expressions <a class="anchor" id="introduction"></a>

What are __regular expressions__?

* A __regular expression__ (_regex_ or _regexp_) is a powerful tool used for pattern matching and text manipulation.
* It's a sequence of characters that defines a search pattern.

Why are they important in text processing?

* Regular expressions allow you to __search__ for and __modify__ text in a highly flexible and efficient way
* They are __widely used__ in programming, data validation, and data extraction tasks
* Regular expressions provide a concise and expressive way to describe complex patterns in text

Real-world examples of where regular expressions are used:

* __Data validation__: Regular expressions are used to validate user inputs such as email addresses, phone numbers, and ZIP codes.
* __Data extraction__: They help extract specific information from text, like extracting URLs from web pages or dates from documents.
* __Text search and replace__: Regular expressions enable you to find and replace text efficiently in large documents.
* __Log analysis__: They are crucial for parsing and analyzing log files to extract meaningful information.
* __Web scraping__: Regular expressions are used to scrape data from websites by matching patterns in the HTML source code.
* __Programming languages__: Many programming languages and tools support regular expressions for string manipulation.

#### C++ Regular Expression Library <a class="anchor" id="library"></a>

The `<regex>` header in C++:
* The `<regex>` header is a part of the C++ Standard Library, and provides support for regular expressions
    ```c++
    // Include the <regex> header
    #include <regex> 
    using namespace std;
    ```
* It contains classes, functions, and types that allow you to work with regular expressions in C++ programs
* To declare and initialize a `regex` object in C++:
    ```c++
    regex pattern("your_regular_expression_here");
    ```
* The `pattern` is a `regex` object that will hold the regular expression you want to use for matching
* You can customize the regular expression based on your specific needs

### Raw Strings in C++ <a class="anchor" id="raw"></a>

In C++, a raw string is a literal string that is defined using the `R"( ... )"` syntax. This syntax allows you to create string literals without the need for escaping special characters, making it especially useful for strings that contain backslashes and multiple lines of text.

Here's the basic syntax of a raw string in C++:

```c++
R"( your raw string here )"
```

Here are some key features and benefits of raw strings in C++:

* __No escape sequences__: In a raw string, escape sequences like `\"`, `\\`, and `\n` are treated as regular characters and not as escape sequences. This means you can include backslashes without escaping them, making it easier to represent file paths, regular expressions, and other text with backslashes.

* __Multi-line support__: Raw strings can span multiple lines, making it convenient for defining long or multiline strings without the need for explicit line breaks or concatenation.

Here's an example of a raw string in C++ that includes a backslash and multiple lines of text:

```c++
#include <iostream>
#include <string>
using namespace std;

int main() 
{
    string rawString = R"(This is a raw string.
It can contain backslashes \ and span multiple lines.
No need to escape special characters.)";

    cout << rawString << endl;

    return 0;
}
```
In this example, the `R"( ... )"` syntax is used to define a raw string, which can span multiple lines and includes backslashes without the need for escaping.

Raw strings can be especially handy when working with __regular expressions__, file paths, SQL queries, or any text that includes special characters or spans multiple lines. They improve code readability by eliminating the clutter of escape sequences and line concatenations.

Like this:
```c++
regex pattern(R"(your_regular_expression_here)");
```

### Example: Validating an Email Address <a class="anchor" id="email"></a>

A simple program to validate an email address from input. 

[__validate.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture14/validate.cpp)
```c++
#include <iostream>
#include <regex>
#include <string>
using namespace std;

int main() 
{
    string email;
    cout << "Enter an email address: ";
    cin >> email;

    // Define a regular expression pattern for email validation
    regex pattern{R"([a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})"};

    if (regex_match(email, pattern)) 
    {
        cout << "Valid email address!" << endl;
    } 
    else
    {
        cout << "Invalid email address." << endl;
    }

    return 0;
}
```

### Regular Expressions Tutorial <a class="anchor" id="tutorial"></a>

[https://regexone.com/](https://regexone.com/)

Complete lessons 1 through 14.

### Resources <a class="anchor" id="resources"></a>

Testing your regex: [regex101.com](https://regex101.com/)

Reference page:  [regular-expressions](https://cheatography.com/davechild/cheat-sheets/regular-expressions/)

