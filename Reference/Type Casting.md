# Type Casting 
Type Casting helps you to convert one data types to another, for example, let's try to use C-style : 
```c
#include <stdio.h>

int main() {
    double a = 5.5;               //as we see, the variable is double
    int sum = (int)a + 5;         //here with brackets we convert 'a' in int
    printf("Sum is %d", sum);     //print out
    return 0;
}
```
```
Sum is 10
```
In C language we can convert data types in other data types, from ```int``` to ```float```, from ```float``` to ```char```, from pointer to ```void*```. Another example:
```c
#include <stdio.h>

int main() {
    int a = 10;
    double sum = (double)a - 5.3; //converted version : 10.0 - 5.3
    printf("%d", sum)             //Output: 4.7
    return 0;
}
```
But that's all is C-style conversting is unsafe, according C++ Developers. So here's our help :
### - 1️⃣ ```static_cast``` 
#### Helps you to convert one data type to another, safe and good.
```c++
int a = 25; //that's 'int' data type
double b = static_cast<double>(a); //now this variable 'b' has 25.0 from 'a'
```
### - 2️⃣  ```dynamic_cast```
#### Helps you with performing downcasting (converting a pointer/reference of a base class to a pointer/reference of a derived class). 
For example:
```c++
#include <iostream>

class Car {
public:
    virtual void drive() {
        std::cout << "Driving a car" << "\n";;
    }
};

class SportsCar : public Car {
public:
    void drive() override {
        std::cout << "Driving a sports car" << "\n";;
    }

    void boost() {
        std::cout << "Boosting the sports car" << "\n";;
    }
};

int main() {
    Car* carPtr = new SportsCar();
    
    // Attempt to downcast from Car* to SportsCar*
    SportsCar* sportsCarPtr = dynamic_cast<SportsCar*>(carPtr);
    
    if (sportsCarPtr) {   // checking if the object being pointed to is of the SportsCar class or a derived class of SportsCar.
        //if true
        sportsCarPtr->drive(); // Output: Driving a sports car
        sportsCarPtr->boost(); // Output: Boosting the sports car
    } else {
        //if false
        std::cout << "Failed to downcast to SportsCar Class" << "\n";     //if false
    }
    
    delete carPtr;
    return 0;
}
```
### - 3️⃣ ```reinterpret_cast```
#### Helps you with converting one pointer type to another, even if the types are unrelated. 
```c++
#include <iostream>

int main() {
    int num = 10; // Declare and initialize an integer variable num with a value of 10
    
    // Use reinterpret_cast to convert the address of num to a void* pointer
    void* voidPtr = reinterpret_cast<void*>(&num);
    
    // Use reinterpret_cast to convert voidPtr to an double* pointer
    int* intPtr = reinterpret_cast<double*>(voidPtr);
    
    // Dereference intPtr to access the value of num and print it to the console
    std::cout << "Value of num: " << *intPtr <<  "\n";

    return 0;
}

```
### - 5️⃣ ```const_cast```
#### Helps you with removing ```const``` from variables
```c++
#include <iostream>

int main() {
    const int num = 10;                               //creating a variable
    const int* constPtr = &num; //pointing at variable's adress, so we can change the original

    int* intPtr = const_cast<int*>(constPtr); //removing const
    *intPtr = 20;                                      // changing original value through pointer

    std::cout << "Modified value of num is " << num << "\n"; //Output : Modified value of num is 20

    return 0;
}

```
Be careful with ```const_cast``` 🤫
