---
layout: default
permalink: lab/8
---

# Lab 8: Regular Expressions in C++ and Linux

## Instructions
* First read this page then start working on lab with the GitHub classroom link below.

* Use the code in the GitHub repository for this lab.

* Github Classroom Link: [https://classroom.github.com/a/HiREPVtw](https://classroom.github.com/a/HiREPVtw)

## Objective

Understand the basics of regular expressions and how to use them. Through practical examples, learn how regex can be helpful for data related tasks like validation and searching.

## Preliminaries

There are three functions that are a part of the `<regex>` library. [https://en.cppreference.com/w/cpp/regex](https://en.cppreference.com/w/cpp/regex)

* `regex_match`
    - Attempts to match a regular expression to an entire character sequence

```c++
    string email = "dbalash@richmond.edu";

    // Regular expression pattern for email validation
    regex pattern{R"([a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})"};

    if (regex_match(email, pattern)) 
    {
        cout << "Valid email address!" << endl;
    } 
```

* `regex_search`
    -  Attempts to match a regular expression to any part of a character sequence

```c++
string stringToSearch = "Hello, World!";
smatch stringMatches;
regex regexPattern(R"((\w+))");  // Match a word

if (regex_search(stringToSearch, stringMatches, regexPattern)) 
{
    cout << "First word: " << stringMatches[0] << endl;
}
```

* `regex_replace`
    - Replaces occurrences of a regular expression with formatted replacement text 

```c++
string stringToModify = "cats are great, I love cats!";
regex regexPattern(R"(cats)");
string replacement = "dogs";
string result = regex_replace(stringToModify, regexPattern, replacement);
cout << result;  // "dogs are great, I love dogs!"
```



## Part 1: Password Strength Checker

* Write a program that checks the strength of a user's password. 

* The password is considered strong if it:
    - Contains at least __6__ characters 
    - Contains at most __20__ characters.
    - Contains at least one __lowercase__ letter
    - Contains at least one __uppercase__ letter
    - Contains at least one __digit__
    - Does __not contain three__ repeating characters in a row, like "aaa"

* __Hint__: You might need multiple regex patterns to verify these conditions.

* __Hint__: For the three repeating characters in a row.
    - See Lesson 15 on __back referencing__ 
    - [https://regexone.com/lesson/misc_meta_characters](https://regexone.com/lesson/misc_meta_characters)

* Start with the code in the file `password.cpp`

* Implement the `isStrongPassword` function. 


## Part 2: Analyzing a web server log file
Imagine you're a system administrator for a web server. You need to analyze the server's access logs to monitor and respond to specific types of requests. Let's consider a simplified version of the Common Log Format, which looks like this:

Excerpt from the file __webserver.log__ available in repository.
```
127.0.0.1 - a3b2c1d [10/Oct/2023:13:55:36 -0700] "GET /index.html HTTP/1.0" 200 2326
10.0.0.5 - f4g5h6i7 [10/Oct/2023:13:56:40 -0700] "POST /submit-data HTTP/1.0" 503 1226
192.168.1.102 - j8k9l0m [10/Oct/2023:14:02:20 -0700] "GET /images/photo.jpg HTTP/1.1" 404 762

```
Each log entry includes:
* Client IP address
* User ID (if HTTP authentication was performed)
* Date, time, and timezone
* Request line from the client in double quotes
* Status code returned to the client
* Size of the object returned to the client

<div class="requirement">
For each of the following, put the Linux bash shell command that you used along with the results in the README.md file for this lab. 
</div>

Do the following:
* Extract all 404 errors
    - Find all requests that resulted in a 404 status code (File Not Found)
* Find all image requests
    - Find all requests made to image files (.jpg, .png, and .gif)
* Identify all POST requests
    - Find all POST requests made to the server
* List all unique IPs
    - List all unique IP addresses that have accessed the server

__Hint__: Use the `grep -E` command to search the log.
```shell
grep -E 'YOUR REGEX HERE' webserver.log
```

__Hint__: Use the `grep -E -o` command to search the log and only return the matched string.
```shell
grep -E -o 'YOUR REGEX HERE' webserver.log
```

__Hint__: You can _pipe_ the output of your grep command to other unix commands such as `sort` or `uniq`.
```shell
grep -E -o 'YOUR REGEX HERE' webserver.log | sort | uniq
```

__NOTE__: the `\d` does not work with grep, use `[0-9]` instead.

## Part 3: Searching for Failed Authentication Attempts in an OpenSSH Log

Imagine you're managing a server and you're monitoring the SSH log for security. You have a log file named `auth.log` with entries like:

Excerpt from the file __auth.log__ available in repository.
```
Dec 10 07:28:08 LabSZ sshd[24247]: Failed password for root from 112.95.230.3 port 55618 ssh2
Dec 10 07:28:08 LabSZ sshd[24247]: Received disconnect from 112.95.230.3: 11: Bye Bye [preauth]
Dec 10 07:28:08 LabSZ sshd[24249]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=112.95.230.3  user=root
Dec 10 07:28:10 LabSZ sshd[24249]: Failed password for root from 112.95.230.3 port 57138 ssh2
Dec 10 07:28:10 LabSZ sshd[24249]: Received disconnect from 112.95.230.3: 11: Bye Bye [preauth]
```

<div class="requirement">
For each of the following, put the Linux bash shell command that you used along with the results in the README.md file for this lab. 
</div>

* You want to identify all failed login attempts, and for this purpose, you specifically want to extract:
    - The timestamp.
    - The user for which the login failed.
    - The IP address from which the login attempt was made.

Using grep, extract pertinent information about failed SSH login attempts from the `auth.log`, helping in identifying potential unauthorized access attempts.

Example output:
```
Dec 10 09:11:26 LabSZ sshd[24437]: Failed password for invalid user admin from 185.190.58.151 port 44155 ssh2
Dec 10 09:11:28 LabSZ sshd[24443]: Failed password for invalid user user from 103.99.0.122 port 62581 ssh2
Dec 10 09:11:31 LabSZ sshd[24445]: Failed password for root from 103.99.0.122 port 49486 ssh2
```

## Part 4: Search and Replace

Use C++ and the regex library to search and replace from an HTML string.

__Tasks__: 
* Edit the `replace.cpp` file in the `Part4` directory in the repository
* Modify the provided C++ code to replace all links starting with `/local/` with links starting with `https://newsite.com/`

__Hint__: Use a `regex` pattern and the `regex_replace` function.

__Expected Output__: When the modified code runs, it should print the HTML with the updated links.

```
<!DOCTYPE html>
<html>
<head>
    <title>Sample Page</title>
</head>
<body>
    <h1>Welcome to the Sample Page</h1>
    <p>Here are some links:</p>
    <ul>
        <li><a href="https://www.example.com">Example</a></li>
        <li><a href="http://www.testsite.com/page1">Test Site</a></li>
        <li><a href="https://newsite.com/link1">Local Link 1</a></li>
        <li><a href="https://newsite.com/link2">Local Link 2</a></li>
    </ul>
    <p>Thank you for visiting!</p>
</body>
</html>
```

