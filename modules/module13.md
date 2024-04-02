---
layout: default
permalink: module/13
---

# Module 13: REST API - Part 3

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/gnX89gd6](https://classroom.github.com/a/gnX89gd6)

## Resources

[Crow API documentation](https://crowcpp.org/master/reference/annotated.html)


## Exercise 1: 

1. Review the code in the GitHub repository. Take note of the changes since module 12, including additional functionality to __sort__, __search__, and __filter__ toppings in the `toppingFunctions.cpp` file. Also take note of a new member variable in the file `Toppings.h`.
2. Use the Thunder Client to test the new functionality by using URL parameters for search, sort, and filter(isveg=TRUE).

# Exercise 2
1. Modify the `pizzaSizeFunctions.cpp` to include functionality to __sort__, __search__, and __filter__ sizes based on URL parameters.
2. To do the filter, add a new `bool` private member variable to the `PizzaSize` class in the `PizzaSize.h` file. This `bool` can be called `isThinCrust`. You will need to modify other places in the code to make sure you include this new value, like when you convertToJson. 
3. Use the Thunder Client to test the new functionality by using URL parameters for search, sort, and filter(isthincrust=TRUE).


