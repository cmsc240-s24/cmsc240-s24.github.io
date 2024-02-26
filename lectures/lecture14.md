---
layout: default
permalink: /lectures/14
---

# Lecture 14: Memory Leaks and Memory Violations

### Objective
Gain an understanding of memory leaks and memory violations found in C++ programming. Explore the root causes, consequences, and preventive measures for these issues. Introduce the dynamic analysis tool Valgrind used in detecting, diagnosing, and addressing memory-related problems.


### Lecture Topics

* [Memory Leaks](#leaks)
* [Memory Violations](#violations)
* [Using Valgrind to Detect Memory Leaks and Violations](#valgrind)

#### Memory Leaks <a class="anchor" id="leaks"></a>

In C++, the programmer is responsible for memory management, which includes both the __allocation__ and __deallocation__ of memory. As a result, there are many mistakes that can be made, which is natural considering that all programmers make mistakes. Perhaps the most common mistake is a __memory leak__, where heap allocated memory is not freed.  

* __Memory leak__: Memory that is no longer reachable or usable but hasn't been deallocated.
* Causes of memory leaks:
    - Dynamically allocated memory not freed
    - Pointers going out of scope without deleting their memory
    - Repeated allocations without deallocations
* Consequences of memory leaks
    - Decreased available memory
    - Reduced application performance
    - Crashes and unpredictable behavior

##### Example: Dynamically allocated memory not freed

[__memleak.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Leaks/memleak.cpp)
```c++
int main() 
{
    // Dynamically allocate an array of 100 integers
    int* arr = new int[100];  

    // Do something with the array 
    for (int i = 0; i < 100; i++) 
    {
        arr[i] = i;
    }

    return 0;
}
```

##### Example: Pointers going out of scope without deleting their memory

[__memscope.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Leaks/memscope.cpp)
```c++
#include <iostream>

double* calculate(int resultSize, int max)
{
    double* values = new double[max];

    double* results = new double[resultSize];

    /* the results calculated using values */


    return results;
}

int main() 
{
    double* result = calculate(100, 1000);
    
    for (int i = 0; i < 100; i++) 
    {
        std::cout << result[i] << std::endl;
    }

    delete[] result;

    return 0;
}
```

##### Example: Repeated allocations without deallocations
[__memrepeat.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Leaks/memrepeat.cpp)
```c++
#include <iostream>

int main() 
{
    int* ptr = nullptr;

    for (int i = 0; i < 10; i++) 
    {
        // Allocate memory for an integer
        ptr = new int;   

        // Assign the value of i to the allocated memory
        *ptr = i;            

        std::cout << *ptr << " " << std::endl;
    }

    delete ptr;

    return 0;
}
```


#### Memory Violations <a class="anchor" id="violations"></a>

* __Memory violation__: scenarios where a program accesses memory locations that it's not supposed to. These violations can lead to undefined behavior, program crashes, data corruption, or even security vulnerabilities.
* Types of memory violations
    - Buffer overflow: Accessing memory beyond the allocated region.
    - Buffer underflow: Accessing memory before the start of an allocated region.
    - Dangling pointers: Pointers that point to memory that has been deallocated.
    - Invalid memory access: Accessing memory chunks which were never allocated.
* Consequences of memory violations
    - Undefined behavior
    - Data corruption
    - Crashes
    - Security vulnerabilities

##### Example: Buffer overflow

[__overflow.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Violations/overflow.cpp)
```c++
int main() 
{
    // Dynamically allocate space for 5 integers on the heap
    int* buffer = new int[5]; 

    // This loop will overflow the buffer when i == 5
    for (int i = 0; i <= 5; i++) 
    {
        buffer[i] = i;
    }

    // Free the allocated memory
    delete[] buffer;  

    return 0;
}
```

##### Example: Dangling pointers

[__dangling.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Violations/dangling.cpp)
```c++
int main() 
{
    // Dynamically allocate an integer and make 'ptr' point to it
    int* ptr = new int[5];  

    // Deallocate the memory
    delete[] ptr;  

    // 'ptr' now becomes a dangling pointer 
    // since it still holds the address of the deallocated memory

    // Accessing memory through a dangling pointer, leading to undefined behavior
    *ptr = 10;  

    return 0;
}
```

It's a good practice to set pointers to `nullptr` after deleting to prevent such situations:
```c++
delete[] ptr;
ptr = nullptr;  
```

##### Example: Invalid memory access
[__invalidaccess.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Violations/invalidaccess.cpp)
```c++
int main() 
{
    // Pointer not pointing to any valid memory location
    int* ptr = nullptr;  

    // Trying to write to an invalid memory location
    *ptr = 5;  

    return 0;
}
```



#### Using Valgrind to Detect Memory Leaks and Violations <a class="anchor" id="valgrind"></a>

__Valgrind__ is a versatile dynamic analysis tool which is specifically designed to detect memory management problems in C++ programs, including __memory leaks__ and various __memory violations__.

* Types of issues detected
    - Memory leaks: Memory that the program allocates but never deallocates.
    - Invalid memory access: This includes reading or writing memory that was never allocated, or accessing memory after it's been freed.
    - Reading uninitialized memory: Using the value stored in uninitialized memory.
    - Incorrect freeing of memory: Like double-deleting.

Let’s look at a few examples of using __valgrind__ to debug some obvious memory leaks.

##### Debugging a memory leak with valgrind

Consider the incorrect code below:

[__memleak.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Valgrind/memleak.cpp)
```c++
#include <iostream>
using namespace std;

int main()
{
    int* ptr = new int;
    
    *ptr = 50;

    cout << "Contents of pointer == " << *ptr << endl;

    ptr = new int; //<-- memory leak

    delete ptr;

    return 0;
}
```

This example is a bit obvious, but it’s almost always not this clear why you have a __memory leak__. 

So we can turn our attention to __valgrind__, but before, we should compile our program with debugging symbols using `-g`.

```
g++ -g memleak.cpp -o memleak
```
This gives __valgrind__ access to the exact line of code and variable names to give you more information about what is wrong. After compiling the program, you run it like so:

```
valgrind ./memleak
```

Getting the following output:
```
==99494== Memcheck, a memory error detector
==99494== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==99494== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==99494== Command: ./memleak
==99494== 
Contents of pointer == 50
==99494== 
==99494== HEAP SUMMARY:
==99494==     in use at exit: 4 bytes in 1 blocks
==99494==   total heap usage: 4 allocs, 3 frees, 73,736 bytes allocated
==99494== 
==99494== LEAK SUMMARY:
==99494==    definitely lost: 4 bytes in 1 blocks
==99494==    indirectly lost: 0 bytes in 0 blocks
==99494==      possibly lost: 0 bytes in 0 blocks
==99494==    still reachable: 0 bytes in 0 blocks
==99494==         suppressed: 0 bytes in 0 blocks
==99494== Rerun with --leak-check=full to see details of leaked memory
==99494== 
==99494== For lists of detected and suppressed errors, rerun with: -s
==99494== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
```
Notice that it clearly says that 4 bytes were __definitely lost__. And it even helpfully tells you to rerun your program with `--leak-check=full` to see details of leaked memory. So let’s do that, and we get the additional information:

```
valgrind --leak-check=full ./memleak
```

```
==99742== 4 bytes in 1 blocks are definitely lost in loss record 1 of 1
==99742==    at 0x4C388C3: operator new(unsigned long) (vg_replace_malloc.c:422)
==99742==    by 0x400937: main (memleak.cpp:6)
```

This says: the memory that was lost was allocated using `new` operator on line 6 of our program. Looking at our program we see exactly where that occurred, and this allows us to fix it. Unfortunately, though, it can’t tell us where to put the `delete`, but it does tell us that we need to do so somewhere.

##### Debugging a memory violation using valgrind 

To see an example of a memory violation, let’s look at another incorrect program.

[__memviolation.cpp__](https://github.com/cmsc240-f23/code/blob/main/lecture13/Valgrind/memviolation.cpp)
```c++
#include <iostream>
using namespace std;

int main()
{
    int* ptr = new int;
    
    *ptr = 50;

    cout << "*ptr == " << *ptr << endl;

    delete ptr;

    *ptr = 20; //<-- memory violation (accessing invalid memory)

    cout << "*ptr == " << *ptr << endl; //<-- memory violation (accessing invalid memory)
 
    delete ptr; //<-- memory violation (double delete)

    return 0;
}
```

Notice that we dereference and assign to `*ptr` after deleting `ptr`, then later we again dereference when using `cout`, and then again, we double delete `ptr` (it’s already been deleted!). This is a slew of memory violation, and __valgrind__ will identify all of these. Let’s look at the output:

```
g++ -g memviolation.cpp -o memviolation

valgrind ./memviolation 
```

```
==101140== Memcheck, a memory error detector
==101140== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==101140== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==101140== Command: ./memviolation
==101140== 
*ptr == 50
==101140== Invalid write of size 4
==101140==    at 0x40098A: main (memviolation.cpp:14)
==101140==  Address 0x5b4dc80 is 0 bytes inside a block of size 4 free'd
==101140==    at 0x4C3B299: operator delete(void*, unsigned long) (vg_replace_malloc.c:935)
==101140==    by 0x400985: main (memviolation.cpp:12)
==101140==  Block was alloc'd at
==101140==    at 0x4C388C3: operator new(unsigned long) (vg_replace_malloc.c:422)
==101140==    by 0x400937: main (memviolation.cpp:6)
==101140== 
==101140== Invalid read of size 4
==101140==    at 0x4009A6: main (memviolation.cpp:16)
==101140==  Address 0x5b4dc80 is 0 bytes inside a block of size 4 free'd
==101140==    at 0x4C3B299: operator delete(void*, unsigned long) (vg_replace_malloc.c:935)
==101140==    by 0x400985: main (memviolation.cpp:12)
==101140==  Block was alloc'd at
==101140==    at 0x4C388C3: operator new(unsigned long) (vg_replace_malloc.c:422)
==101140==    by 0x400937: main (memviolation.cpp:6)
==101140== 
*ptr == 20
==101140== Invalid free() / delete / delete[] / realloc()
==101140==    at 0x4C3B299: operator delete(void*, unsigned long) (vg_replace_malloc.c:935)
==101140==    by 0x4009CF: main (memviolation.cpp:18)
==101140==  Address 0x5b4dc80 is 0 bytes inside a block of size 4 free'd
==101140==    at 0x4C3B299: operator delete(void*, unsigned long) (vg_replace_malloc.c:935)
==101140==    by 0x400985: main (memviolation.cpp:12)
==101140==  Block was alloc'd at
==101140==    at 0x4C388C3: operator new(unsigned long) (vg_replace_malloc.c:422)
==101140==    by 0x400937: main (memviolation.cpp:6)
==101140== 
==101140== 
==101140== HEAP SUMMARY:
==101140==     in use at exit: 0 bytes in 0 blocks
==101140==   total heap usage: 3 allocs, 4 frees, 73,732 bytes allocated
==101140== 
==101140== All heap blocks were freed -- no leaks are possible
==101140== 
==101140== For lists of detected and suppressed errors, rerun with: -s
==101140== ERROR SUMMARY: 3 errors from 3 contexts (suppressed: 0 from 0)
```

* First, notice that at the end it lists 3 errors, which match up to the three violations in the code. 

* Then above, the first of these errors is an invalid write. This occurs when we `*ptr = 20;` because ptr is already deleted. 

* The second error is an invalid read when we use `*ptr` in our `cout`.

* Finally, the third error, is a invalid `delete` when we `delete ptr;` for the second time. 

* __Valgrind__ notes the location in code these events occurred at, which gives us a start on fixing our code, but we still have to reason about why there is an error. 

Valgrind is an invaluable tool for C++ developers aiming to ensure their programs are free of memory-related issues. Properly used, it can help identify, diagnose, and resolve these issues long before they become critical problems or vulnerabilities.


