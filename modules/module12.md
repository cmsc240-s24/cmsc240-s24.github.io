---
layout: default
permalink: module/12
---

# Module 12: REST API - Part 2

* First read this page then start the module with the GitHub classroom link below.
* Github Classroom Link: [https://classroom.github.com/a/2W82s5Oa](https://classroom.github.com/a/2W82s5Oa)

## Resources

[Crow API documentation](https://crowcpp.org/master/reference/annotated.html)


## Exercise 1: 

1. Review the code in the GitHub repository. Take note of the changes since module 11, including the relocation of the toppings handler functions to the `toppingFunctions.cpp` file. Also take note of a new class file `PizzaSize.h`.
2. Notice the new map in the `pizzaAPI.cpp` that will store the size of the pizza.
    ```c++
    // Creating a map to store pizza sizes
    map<string, PizzaSize> pizzaSizesMap;
    ```
3. Create a new endpoint to __read__ this new resource. The endpoint should return all of the available pizza sizes and should use the HTTP method: `GET`. Add your code in the `pizzaAPI.cpp` where it says: ` // Exercise 1: Add new end points here...`
4. Test your new endpoint.
5. Create a new endpoint to __read__ a single instance of the resource. The endpoint should return one of the available pizza sizes based on an id and should use the HTTP method: `GET`.
6. Test your new endpoint.
7. Create a new endpoint to __update__ a single instance of the resource. The endpoint should modify one of the available pizza sizes based on an id and should use the HTTP method: `PUT`. A JSON body should be provided in the request.
    ```json
    {"id":"1","size":"Mini"}
    ```
8. Test your new endpoint.
9. Create a new endpoint to __create__ a single instance of the resource. The endpoint should create a new pizza sizes and should use the HTTP method: `POST`.A JSON body should be provided in the request.
    ```json
    {"id":"4","size":"Mega-Large"}
    ```
10. Test your new endpoint
11. Create a new endpoint to __delete__ a single instance of the resource. The endpoint should return one of the available pizza sizes based on an id and should use the HTTP method: `DELETE`.
12. Test your new endpoint.


## Exercise 2: 
1. Add a new function to `pizzaAPI.cpp` that will save the PizzaSize map to a file. 
    ```c++
    void saveToFile(std::map<std::string, PizzaSize> data, std::string filename)
    ```
2. Implement the save to file function.
3. Call the function where it says: `//  Exercise 2: Add code here to save the resources to a file.`
4. Test this function by starting and stopping the pizzaAPI program.

__Hint__:
```c++
json::wvalue convertPizzaSizeToJson(PizzaSize pizzaSize) 
{
    json::wvalue writeValueJson;
    writeValueJson["id"] = pizzaSize.getId();
    writeValueJson["size"] = pizzaSize.getSize();
    return writeValueJson;
}


void saveToFile(map<string, PizzaSize> data, string filename)  
{
    // Open the file for writing
    ofstream file(filename);

    if (file.is_open()) 
    {
        // Create a new JSON write value use to write to the file.
        json::wvalue jsonWriteValue;
        
        // For each object in the map, convert the object to JSON and add to the write value.
        int index = 0;
        for (pair<string, PizzaSize> keyValuePair : data)
        {
            // first: gives you access to the first item in the pair.
            // second: gives you access to the second item in the pair.
            jsonWriteValue[index] = convertPizzaSizeToJson(keyValuePair.second);
            index++;
        }

        // Write the JSON to the file.
        file << jsonWriteValue.dump();
        file.close();
    }
}
```



## Exercise 3: 
1. Add a new function to `pizzaAPI.cpp` that will load the PizzaSize map from a file. 
    ```c++
    map<string, PizzaSize> loadFromFile(string filename)
    ```
2. Implement the load from file function.
3. Call the function where it says: `// Exercise 3: Add code here to read data from a file....`
4. Test this function by starting and stopping the pizzaAPI program.


__Hint:__
```c++
map<string, PizzaSize> loadFromFile(string filename) 
{
    map<string, PizzaSize> data;
    
    // Open the file for reading.
    ifstream file(filename);

    // If the file is open. 
    if (file.is_open()) 
    {      
        // Create a stream for reading in the file.
        ostringstream stringStreamJson;

        // Read the entire JSON string.
        stringStreamJson << file.rdbuf();

        // Load the string into a JSON read value object.
        json::rvalue jsonReadValue = json::load(stringStreamJson.str());

        // Close the file.
        file.close();

        // For each item in the JSON convert it to an object, 
        // and add it to the data map.
        for (json::rvalue item : jsonReadValue) 
        {
            PizzaSize pizzaSize{item["id"].s(), item["size"].s()};
            data[pizzaSize.getId()] = pizzaSize;
        }
    }
    
    return data;
}
```









