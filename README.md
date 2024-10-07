# Assignment 3 - CS 311 Fall 2024

**Author:** Ivy Swenson  
**Started:** 2024-09-21  
**Last Updated:** 2024-09-26  

## Overview
This project includes a set of functions for CS 311 Assignment 3. It focuses on implementing fundamental algorithms and templates in C++, including a `gcd` function for calculating the greatest common divisor using the Euclidean algorithm and a `lookup` template function for retrieving elements from a linked list by index. The project is designed to demonstrate understanding of recursion, template functions, and exception handling in C++.

## Diagram
![image](https://github.com/user-attachments/assets/a4e6a7b8-9877-475b-9c06-5581b4eab7bb)

## Files
- **`da3.hpp`**: Header file that contains function declarations and template definitions for:
  - `gcd`: A function for calculating the greatest common divisor of two integers.
  - `lookup`: A template function for retrieving elements from a singly linked list by index.
  - `didItThrow`: A function to test whether a given function throws an exception.
- **`da3.cpp`**: Implementation file with the source code for the functions declared in `da3.hpp`.
- **`LLNode.hpp`**: Header file for the `LLNode` class template, representing nodes in a singly linked list.
- **`da3_test.cpp`**: Test file containing unit tests for `gcd`, `lookup`, and `didItThrow` functions, using the `doctest` testing framework.
- **`doctest.h`**: Header file for the `doctest` library, used to facilitate testing of the functions.

## Functionality
### 1. `gcd` Function
Calculates the greatest common divisor (GCD) of two integers using a recursive approach. It follows the Euclidean algorithm, which finds the GCD of two numbers by recursively replacing the larger number with the remainder of dividing the two numbers, until one of the numbers becomes zero:

```cpp
int gcd(int a, int b);
```

- **Parameters**:  
  - `a`: An integer value.
  - `b`: An integer value.
- **Returns**:  
  The greatest common divisor of `a` and `b`. If both `a` and `b` are zero, it returns 1 as a special case.

- **Example**:
    ```cpp
    int result = gcd(48, 18); // result will be 6
    ```

### 2. `lookup` Template Function
Retrieves an element by its index from a singly linked list. It is implemented as a function template to allow lists of different types:

```cpp
template <typename ValueType>
ValueType lookup(const LLNode<ValueType>* head, std::size_t index);
```

- **Parameters**:  
  - `head`: A pointer to the head of a singly linked list (`LLNode<ValueType>`).
  - `index`: A zero-based index indicating the position of the element to retrieve.
- **Returns**:  
  The value of the node at the specified index. Throws `std::out_of_range` if the index is greater than the length of the list.
  
- **Example**:
    ```cpp
    LLNode<int>* list = new LLNode<int>(1);
    list->_next = new LLNode<int>(2);
    list->_next->_next = new LLNode<int>(3);
    int value = lookup(list, 1); // value will be 2
    ```

### 3. `didItThrow` Function
Tests whether a given function throws an exception during execution. It uses a `std::function` object to accept any callable, such as lambda functions or other function objects:

```cpp
void didItThrow(const std::function<void()>& ff, bool& threw);
```

- **Parameters**:  
  - `ff`: A `std::function<void()>` that represents the function to execute.
  - `threw`: A reference to a boolean variable that will be set to `true` if an exception is thrown during the execution of `ff`, and `false` otherwise.
  
- **Example**:
    ```cpp
    bool threw;
    didItThrow([]() { throw std::runtime_error("Test error"); }, threw);
    // threw will be true after this call
    ```

## How to Compile and Run
To compile the project, you can use a C++ compiler like `g++`. Make sure you include all the necessary files:

```bash
g++ -std=c++17 -o da3 da3.cpp da3_test.cpp
```

This command compiles `da3.cpp` and `da3_test.cpp` into an executable file named `da3`.

To run the compiled executable:
```bash
./da3
```

If you are using the `doctest` testing framework, running this executable will also run the tests defined in `da3_test.cpp` and provide the results in the terminal.

## Example Usage
Below is an example program that demonstrates the use of the functions provided in this project:

```cpp
#include "da3.hpp"
#include "LLNode.hpp"
#include <iostream>

int main() {
    // Example usage of gcd
    int gcdResult = gcd(56, 98);
    std::cout << "GCD of 56 and 98 is: " << gcdResult << std::endl;

    // Create a simple linked list and use lookup
    LLNode<int>* list = new LLNode<int>(10);
    list->_next = new LLNode<int>(20);
    list->_next->_next = new LLNode<int>(30);
    try {
        int value = lookup(list, 2);
        std::cout << "Element at index 2 is: " << value << std::endl;
    } catch (const std::out_of_range& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }

    // Example usage of didItThrow
    bool threw;
    didItThrow([]() { throw std::logic_error("Sample error"); }, threw);
    std::cout << "Did it throw? " << (threw ? "Yes" : "No") << std::endl;

    return 0;
}
```

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments
- **Instructor**: Special thanks to the CS 311 course instructor for guidance on the project.
- **doctest**: The testing framework `doctest` was used to facilitate unit testing.
- **Classmates**: Thanks to my classmates for their collaboration and support.
