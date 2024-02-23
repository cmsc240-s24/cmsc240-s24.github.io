---
layout: default
permalink: lab/6
---

# Lab 6: Inheritance and Polymorphism

### Instructions
* In this lab you will work in **teams of two**, though each of you needs to commit and push to **your own individual GitHub repository**. There may be one group of size three. You will use the technique of **pair programming**, see description at the bottom of this page.

* Write the names of each team member at the top of your README.md file in your individual repositories. 

* First read this page then start coding the lab with the GitHub classroom link below.

* Put your code in the GitHub repository for this lab.

* Github Classroom Link: [https://classroom.github.com/a/sZsMbP3e](https://classroom.github.com/a/sZsMbP3e)


### Objective
Design and implement an inventory system to manage different types of wearable tech products using __inheritance__ and __polymorphism__.

## Wearable Tech Inventory System

### Problem Statement:
A tech store sells various wearable devices such as smartwatches, fitness trackers, and augmented reality (AR) glasses. These devices have some common attributes, but each also has unique features.

#### Base Class - __WearableDevice__:

- Data Members:
   - `brand`: a string representing the device's brand.
   - `price`: a float representing the device's price.
   - `quantity`: an int representing the number of units in stock.
- Member Functions:
   - `getInfo()`: Virtual function to print device details.
   - `sell(int units)`: Reduce the quantity by a specified number of units.
   - `restock(int units)`: Increase the quantity by a specified number of units.


#### Derived Classes

- __Smartwatch__:
   - Additional Data Members:
      - `screenSize`: a float representing the display size in inches.
      - `hasGPS`: a boolean indicating if the watch has GPS.
      - Overrides `getInfo()` to include screen size and GPS information.

- __FitnessTracker__:
   - Additional Data Members:
      - `heartRateMonitor`: a boolean indicating if it has a heart rate monitor.
      - `batteryLife`: an int representing battery life in hours.
      - Overrides `getInfo()` to include heart rate monitor and battery life.

- __ARGlasses__:
   - Additional Data Members:
      - `fieldOfView`: an int representing the field of view in degrees.
      - `interactiveSurface`: a boolean indicating if it projects interactive surfaces.
      - Overrides `getInfo()` to include field of view and interactive surface details.

<div class="requirement">
Review the code in testdevices.cpp, WearableDevice.h, and WearableDevice.cpp.  Then write the code for the classes ARGlasses, FitnessTracker, and SmartWatch using the problem statement description above.  Your new classes should extend the WearableDevice class to inherit the functionality. I have created the `.cpp` and `.h` files in the lab repository, and you should write your code where it says `// Write your code here...`

When you finish and test your code by running the main function in the testdevices.cpp file.

```shell
$ g++ ARGlasses.cpp FitnessTracker.cpp SmartWatch.cpp WearableDevice.cpp testdevices.cpp -o testdevices

$ ./testdevices 
```

Here is a sample of what the output should look like
```
Brand: Apple
Price: $399.99
Quantity: 10
Screen Size: 1.7 inches
GPS: Yes
-------------------------------
Brand: Fitbit
Price: $149.99
Quantity: 15
Heart Rate Monitor: Yes
Battery Life: 24 hours
-------------------------------
Brand: MagicLeap
Price: $2295
Quantity: 5
Field of View: 50 degrees
Interactive Surface: Yes
-------------------------------
Selling 3 Apple smartwatches...
Remaining stock for Apple smartwatch: 7
Restocking 5 Fitbit trackers...
New stock for Fitbit tracker: 20
```
</div>

+

<div class="requirement">
When you finish writing and testing the code. In your README.md file write a brief description of how the testdevices.cpp file is using polymorphism. 
</div>

+

<div class="requirement">
Draw a UML diagram of the completed inventory system.  Include a picture of your diagram in the repository. Put the name of your diagram file in the README.md so we know what to look for when grading.
</div>


## Grading Rubric

### Total Points: 100

- Functionality (30 points)
   - Correctness (20 points)
      - Code produces expected output: ___/10
      - Code handles edge cases appropriately: ___/10
   - Efficiency (5 points)
      - Code runs within expected time limits: ___/5
   - Error Handling (5 points)
      - Code gracefully handles unexpected inputs or scenarios without crashing: ___/5
- Completeness (40 points)
   - All required functionality is implemented: ___/40
- Code Quality (30 points)
    - Readability (10 points)
        - Code has meaningful variable and function names: ___/5
        - Code is consistently formatted and indented: ___/5
    - Modularity (10 points)
        - Code is appropriately divided into functions: ___/5
        - Each function has a single responsibility: ___/5
    - Documentation (10 points)
        - Code includes a header comment explaining the program's purpose: ___/3
        - Each function has a comment explaining its purpose, inputs, and outputs: ___/5
        - Inline comments explain non-obvious sections of the code: ___/2


## Pair programming

Pair programming is a software development technique in which two programmers work together at one computer. One, the **driver**, writes code while the other, the **navigator**, reviews each line of code as it is typed in. **The two programmers switch roles frequently.**

