# Raw Pointers
Raw pointers are often used where you need to manage memory by hand, such as when working with dynamic memory allocation or interacting with external libraries.
Here are a few common use cases:
- **Dynamic memory allocation**: Raw pointers are often used to allocate memory allocations dynamically with other delete operators. Example:
```c++
int* arr = new int[5]; // Allocating an array of integers
// Use the 'arr' pointer to access and manipulate the allocated memory
delete[] arr; // Deallocating the memory
```
- **Interfacing with C Libraries**: Raw pointers are often used when interacting with C libraries that expect memory addresses as arguments.
For example, when passing a buffer to a C function:
```c++
char* buffer = new char[100];
c_library_function(buffer); // Pass the memory address to the C library function
delete[] buffer;
  ```
- **Pointer Arithmetic**: Raw pointers allow for pointer arithmetic, which can be useful when working with arrays or iterating over memory blocks.
For example:
```c++
int* ptr = new int[5];
for (int i = 0; i < 5; i++) {
  *(ptr + i) = i; // Assigning values to the array elements using pointer arithmetic
}
delete[] ptr;
```

## new and delete[]
In C++, the ```new``` and ```delete``` operators are used for dynamic memory allocation and deallocation, respectively. 
They allow you to allocate memory at runtime and release it when it is no longer needed. 
The ```delete[]``` operator is specifically used to deallocate memory that was allocated using the ```new[]``` operator for arrays.

## <br>Explanation of ```new```, ```delete```, and ```delete[]```:</br>

### ```new``` Operator:
- 1️⃣ The new operator is used to dynamically allocate memory for a single object or an array.
- 👇 When used for a single object, it allocates memory and returns a pointer to the allocated memory.
- ⚖️ When used for an array, it allocates memory for multiple objects and returns a pointer to the first element of the array.
**The syntax for using new is**:
```
pointer_variable = new data_type;
```
 or
 ```
 pointer_variable = new data_type[size];
```
Example 1. Allocating memory for a single object
```c++
int* ptr = new int; // Allocating memory for a single integer
```
Example 2. Allocating memory for an array
```c++
int* arr = new int[5]; // Allocating memory for an array of 5 integers
 ```
### ```delete``` Operator:
- 🔲The delete operator is often used to deallocate memory that was allocated using ```new``` before.
- 🆓 It frees the memory and makes it available for reuse.
- The syntax for using ```delete``` is:
```c++
delete pointer_variable;
```
Example. Deallocating memory for a single object
```c++
int* arr = new int[5]; // Allocating memory for an array of 5 integers
// Use the allocated memory
delete[] arr; // Deallocating the memory
 ```
But be careful with raw pointers, they're not automated as Smart Pointers, so you need to clean after yourself using ```delete``` or ```delete[]```. 🤫
# 🫠 Memory Leakage :
Memory leakage refers to a situation in which a computer program fails to release memory that it no longer needs, resulting in the loss of available memory resources. 
This can occur when dynamically allocated memory is not properly deallocated or released after it is no longer needed.

<br>Memory leakage can lead to a gradual reduction in available memory, which can eventually cause the program or system to run out of memory. </br>
This can result in degraded performance, crashes, or even system failures.

There are several common causes of memory leakage:
- **Forgetting to deallocate dynamically allocated memory**: When memory is allocated dynamically using functions like ```malloc()``` or ```new```, it is the responsibility of the programmer to release that memory using ```free()``` or delete respectively.
⚠️ If the programmer forgets to deallocate the memory or if there is a logical error that prevents the deallocation, memory leakage can occur.
- **Circular references**: In languages with automatic garbage collection, such as Java or Python, memory leakage can occur when objects reference each other in a circular manner.
If these objects are not properly released or if the garbage collector is unable to detect the circular reference, the memory occupied by these objects will not be reclaimed.
- **Global variables**: If global variables are used to store dynamically allocated memory and are not properly deallocated, memory leakage can occur.
- Global variables persist throughout the lifetime of the program, so any memory allocated to them will not be released until the program terminates.
Global variables are variables that placed outside blocks/scopes.
<br>Example of global variable : </br>
```c++
#include <iostream>

int x = 5; //global variable, outside any block


void anyFunction(){//block 'anyFunction' starts
  double a = 52.5;  //any code
  int b = 15;
}//block 'anyFunction' ends



int main(){ // block 'main' starts

 // that's inside of block, that's safe here 🙂

} // block 'main' ends
```


To prevent memory leakage, it is important to follow good memory management practices:
- 🥽 Don't forget to deallocate dynamically allocated memory when you don't neet it anymore. Use the appropriate deallocation functions ```delete``` to free the memory.
- 🩻 Avoid circular references between objects, especially in languages with automatic garbage collection.
Break the circular references or use weak references to allow the garbage collector to reclaim the memory.
- 🌐 Minimize the use of global variables and ensure that any memory allocated to them is properly deallocated.
-  🗑 Use memory management tools and techniques provided by the programming language or framework, such as smart pointers or garbage collectors, to automate memory management and reduce the risk of memory leakage.
