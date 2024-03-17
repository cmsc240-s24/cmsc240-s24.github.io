---
layout: default
permalink: module/9
---

# Module 9: Serialization in C++

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/PMii4bAQ](https://classroom.github.com/a/PMii4bAQ)


## Exercise 1: Convert to and from JSON.
In this exercise, you will write a `toJson()` method that will convert a C++ object to JSON document, saving the object state.  And a `fromJson()`method that will convert from a JSON document to a C++ class object. 

Steps:

1. __Setup the environment__: Review the code in the exercise1 directory in the module9 GitHub repository. Make note of the contents of each file, and how the `Makefile` works. 

2. __Implement the `toJson()` function__: In the file `Cat.cpp` implement the `toJson()` function convert an instance of the class to JSON.

3. __Update the `main` function__: In the file `main.cpp` modify the `main` function to call the `toJson()` function for the "_cheddar_" instance of the `Cat` class. After calling the function, save the resulting JSON to a file called `cheddar.json`. 

4. __Compile and test__: Compile and run `program` to test your `toJson()` function.

```shell
$ make
$ ./program
```

From the command line, read the JSON file to confirm that your code worked correctly. 

```shell
$ cat cheddar.json
```

5. __Implement the `fromJson()` function__: In the file `Cat.cpp` implement the `fromJson()` function convert JSON document to an instance of the `Cat` class.

6. __Update the `main` function__: In the file `main.cpp` modify the `main` function to read the `cheddar.json` file. Then call the `fromJson()` function for the "_cheddar_" instance of the `Cat` class. 

7. __Compile and test__: Compile and run `program` to test your `fromJson()` function.

```shell
$ make
$ ./program
```


## Exercise 2: Saving and Loading a `vector` of class objects

In this exercise, you will write a `toJson()` method that will convert a C++ object to JSON document, saving the object state.  And a `fromJson()`method that will convert from a JSON document to a C++ class object. 

Steps:

1. __Setup the environment__: Review the code in the exercise2 directory in the module9 GitHub repository. Make note of the contents of each file, and how the `Makefile` works. 

2. __Implement the `toJson()` function__: In the file `Item.cpp` implement the `toJson()` function convert an instance of the class to JSON.

3. __Update the `main` function__: In the file `main.cpp` modify the `main` function to call the `toJson()` function for _each_ instance of the `Item` class in the `cart` vector. After calling the function, save the resulting JSON to a file called `cart.json`.

__Hint__: review the lecture example:
```C++
    json jsonOutput = json{{"cars", json::array()}};

    for (Car car : cars)
    {
        jsonOutput.at("cars").push_back(car.toJson());
    }

    // Write JSON to a file.
    ofstream outfile("cars.json");
    outfile << jsonOutput.dump(INDENT_SPACES);
    outfile.close();
```

4. __Compile and test__: Compile and run `cart` to test your `toJson()` function.

```shell
$ make
$ ./cart
```

From the command line, read the JSON file to confirm that your code worked correctly. 

```shell
$ cat cart.json
```

5. __Implement the `fromJson()` function__: In the file `Item.cpp` implement the `fromJson()` function convert JSON document to an instance of the `Item` class.

6. __Update the `main` function__: In the file `main.cpp` modify the `main` function to read the `cart.json` file. Then call the `fromJson()` function for _each_ instance of the `Item` class. 

__Hint__: review the lecture example:
```C++
    cars.clear();

    // Read JSON from a file.
    ifstream infile("cars.json");
    json jsonFromFile = json::parse(infile);
    infile.close();

    for (json carJson : jsonFromFile.at("cars"))
    {
        cars.push_back(Car{carJson});
    }
```

7. __Compile and test__: Compile and run `cart` to test your `fromJson()` function.

```shell
$ make
$ ./cart
```

