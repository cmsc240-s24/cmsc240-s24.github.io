---
layout: default
permalink: /lab/5
---

# Lab 5: Enigma 

## Preliminaries

### Github Link

Accept this assignment here: [https://classroom.github.com/a/Xxl1q0yc](https://classroom.github.com/a/Xxl1q0yc)


### Running/Compile your program

You should compile your program using `g++` with the `-Wall` command line option to show all warnings. You will also need to compile multiple .cpp files. The specific command line for compiling is:

```Shell
g++ -Wall usage.cpp comms.cpp Enigma.cpp Rotor.cpp -o comms
```

### Testing your lab

There is a `test.sh` file in the repository to help you test your program.

```Shell
./test.sh
```

If the test script doesn't run initially, you may need to make it executable.

```Shell
chmod u+x test.sh
```


## Enigma Machines (simplified model)

The Enigma machine was used by the Germans in WWII to send encoded messages. At the time, it was a breakthrough in cryptography, and was essentially an extremely advanced substitution cipher. The Enigma machine is also famous for not just being a very advanced cipher, but also because it was broken by none other than Alan Turning, whom many consider the founder of computer science.

In this lab, we will model a simplified version of the Enigma machine. 


### What you need to know for this lab

What you need to know for this lab: Enigma machines used interchangeable rotors that could be placed in different orientations to obtain different substitution patterns. More significantly, the rotors rotated after each character was encoded, changing the substitution pattern and making the code very difficult to break. The behavior of the rotating rotors can be modeled, in a simplified form, by a device consisting of labeled, concentric rings. For example, the picture here has three rings labeled with the letters of the alphabet and '#' (representing a space).

To encrypt a character using this model, find the character on the inner rotor (i.e., the inside ring) and note the character aligned with it on the outer rotor (i.e., the outside ring), then find that character on the middle rotor (i.e., the middle ring) and output the one aligned with it on the outer rotor. After a character is encrypted, turn the inner rotor clockwise one step. Whenever the inner rotor returns to its original orientation, the middle rotor turns once in lock-step, just like the odometer in a car.

<div style="text-align:center">
![](/images/enigma.gif)
</div>

For example, in this configuration the character 'A' would be encrypted as 'N', since 'A' on the inner rotor is aligned with 'H' on the outer rotor, and 'H' on the middle rotor is aligned with 'N' on the outer rotor. After performing this encryption, the inner rotor is rotated clockwise, so the letter 'A' would next be encrypted as 'D'.


Note that decrypting a message requires following the same steps, only in reverse: Find the character on the outer rotor, note the character aligned with it on the middle rotor, find that character on the outer rotor, then output the character aligned with it on the inner rotor. Don't forget to rotate the rotors after each letter is decrypted. The rotor is also rotated clockwise during decryption. 

## Task Requirements

### The Task

You will define a class `Rotor` to simulate the workings of a single rotor, and the class `Enigma` to simulate the workings of an Enigma machine using `Rotor` instances. You will be provided a source code file `comms.cpp` (with a `main` method) as part of the initial material. You should read that file to see how `Enigma` instances are suppose to be used.

**You may not alter `comms.cpp` in any way.** 

Your task is to write both `Enigma` and `Rotor` using proper OOP design with class constructors, information hiding (private members), and encapsulation.

### The `Rotor` Class

The `Rotor` class represents a rotor, including the values of the characters in the rotor and its current orientation (which character is currently on top of the rotor). A good strategy for representing this would be to store the characters in a `string` of length 27 (`#` indicating space) -- index 0 is the top most character. Note that `Rotor`s rotate! And after a full rotation, the next outer rotor rotates (like a odometer in a car). That means you'll need to remember where the rotor started. All of this can lead to some good OOP! :)

For example, your 'Rotor' class should be able to do the following

1.    Be constructed, requiring a `string` that defines the rotor and a single character defining the symbol that should be initially at the top of the rotor. Note: in the constructor, you can call other methods, like the method to rotate to align the rotor to the initial character!
2.    Rotate one click clockwise. This should involve changing the `string`.
3.    Return the index in the `string` at which a given character appears.
4.    Return the character at a given index in the `string`. 

An example of a rotor `String` is `#GNUAHOVBIPWCJQXDKRYELSZFMT` ... which you are to interpret circularly, so that the last character loops around to the first. If you imagine that the first position indicates the top spot on the rotor, then:

`#GNUAHOVBIPWCJQXDKRYELSZFMT` rotated one click clockwise is `T#GNUAHOVBIPWCJQXDKRYELSZFM`

### The `Enigma` Class

This we leave partly up to you. We expect your Engima to have 5 possible rotors, and when your Enigma class is created, it chooses which 3 to use along with their rotor starting symbols. You must hardcode the 5 possible rotors in your class as the following Strings:

1. `#GNUAHOVBIPWCJQXDKRYELSZFMT`
2. `#EJOTYCHMRWAFKPUZDINSXBGLQV`
3. `#BDFHJLNPRTVXZACEGIKMOQSUWY`
4. `#NWDKHGXZVRIFJBLMAOPSCYUTQE`
5. `#TGOWHLIFMCSZYRVXQABUPEJKND`

You must also have encrypt and decrypt methods for encrypting and decrypting strings. These must be compatible with the comms.cpp file that we give you. The behavior in these methods must follow the enigma procedure described above in "Our Simple Model of the Enigma". 

### The `comms` code

**Note you should not edit the `comms.cpp` file**, but you do need to know how it works. 

This is the program's main class, and it is provided for you. The program takes as input (from the command line) the three rotors and their starting characters. A correct call to the program `comms` will provide all the information needed to setup enigma for that encryption/decryption session on the command-line, and the actual string to encrypt/decrypt should be input from standard in.

```
                  ,-- inner rotor initially positioned so X is on top
                  |,-- middle rotor initially positioned so # is on top
                  ||  ,-- outer rotor initially positioned so Y is on top
                  || /
./comms 4 2 3 "X#Y" encrypt
           | | |
           | | `-- outer rotor is rotor 3
           | `-- middle rotor is rotor 2
           `-- inner rotor is rotor 4
```


A couple example runs are here. You must also make your own tests and fully test your code:

```
./comms 1 2 3 "###" encrypt
AAA
NDU
```

```
./comms 3 1 2 "SAT" encrypt
DO#YOUR#BEST#AND#KEEP#ON#KEEPIN#ON
ACAAFAEOZFWKBQKPXZOGIKXTNPEBDXWQCZ
```

```
./comms 5 2 4 "EST" decrypt
CSHIAWDFGDCOE#EZKJHRWAZDDCBCILON#PKUJEXEXSHINZ
THE#NATIONAL#ANIMAL#OF#SCOTLAND#IS#THE#UNICORN
```

## Submission

<div class="requirement">
You must submit

1. `Enigma.h` : `Enigma` class declaration header file
2. `Enigma.cpp` : `Enigma` class member definition file
3.  `Rotor.h` : `Rotor` class declaration header file
4. `Rotor.cpp` : `Rotor` class member definition file
5. `README.md` : Answer questions and describe your work in this lab

Your `Enigma` and `Rotor` classes must meet the specifications above. 

</div>

---

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
   - All required functionality is implemented: ___/20
   - Answered lab questions in the README.md: ___/20
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

---

#### Acknowledgements

This lab was adopted from CS2113 (Spring 2022) at GW.

