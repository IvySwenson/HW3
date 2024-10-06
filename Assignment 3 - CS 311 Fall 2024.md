# Assignment 3 - CS 311 Fall 2024

**Author:** Ivy Swenson  
**Started:** 2024-09-21  
**Last Updated:** 2024-09-26  

## Overview
This project includes a set of functions for CS 311 Assignment 3. It includes a `gcd` function for calculating the greatest common divisor using the Euclidean algorithm, and a `lookup` template function for retrieving elements from a linked list by index.

## Files
- **da3.hpp**: Header file that contains function declarations and template definitions.
- **da3.cpp**: Implementation file with the source code for the functions declared in `da3.hpp`.

## Functionality
### gcd Function
Calculates the greatest common divisor (GCD) of two integers using a recursive approach. It follows the Euclidean algorithm:

```cpp
int gcd(int a, int b);
