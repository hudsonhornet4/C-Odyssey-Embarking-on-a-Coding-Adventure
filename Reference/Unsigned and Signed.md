# Understanding Signed and Unsigned Data Types in C++
## Introduction 📚
  Data types play an important role in how we store and manipulate information in C++. When working with integers, situations are often encountered where the sign of the number is important.
Both ```signed``` and ```unsigned``` data sets give us the flexibility to efficiently handle both positive and negative values.
In this guide, we’ll explore the concept of signed and unsigned data types, their differences, and when to use them effectively. 
Eventually you will have a clearer understanding of how these types of data can affect your code and help you make informed decisions along your programming journey.
Let’s start this exploration together and unlock the potential of signed and unsigned data types in C++. Ready, my stablemate? Let’s start.
- - - - 
### unsigned
In C++, "unsigned" and "signed" are data type modifiers that can be applied to integral data types such as int, short, long, char, etc.
Unsigned and Signed template of declaration: 
```C++
[unsigned or signed] [data type] [name] = [value]
```

- **unsigned**: is used to declare variables that can **only have non-negative values**. They cannot store negative values or represent signed numbers. This modifier effectively extends the range of positive values that a variable can hold.
Example :
```c++
   unsigned int a = 25;
   unsigned short b = 15;
   unsigned int weirdo = -1; 
   ```
If you know that your number is always going to be positive, aka non-negative, then you can/should use ```unsigned```. But if we try to write negative number with ```unsigned```, here's it's variable ```weirdo``` 
and it has -1, which is negative, we will get 4,294,967,295. Why? Since our number is non-positive, then it will go vice-versa and will go from 4,294,967,295 to 0, for example, if we will give ```weirdo``` value -**2**
then we will get 4,294,967,294, and etc. 
### signed
What do we have here? As i understood, ```signed``` is often used only with ```char```.
It only makes a difference with char, because

- It is not defined whether char is signed or unsigned.
- ```char```, ```signed char```, and ```unsigned char``` are three distinct types anyway.

So you should use signed if you need a ```signed char``` (which is probably rarely). Other than that, I can't think of a reason. [[Link]](https://stackoverflow.com/questions/28012943/what-is-the-actual-use-of-signed-keyword "About Signed")
Sometimes we can use our ```char``` to represent numbers, but.. why would we, if have ```int```, ```double``` and other char's bullies? The reason is it's because ```char```'s size is **1 byte**, but ```int```'s size is **4 bytes.**
```c++
unsigned char = 10; //range of unsigned char is 0 to 255.
signed char = -15; //range of signed char is -128 to 127
```
### How to check size of our variables?
 To check sizes of our declared variables, you can use ```sizeof```, which usually returns the size in byes of data type or variable.
 Let's check:
 We can try to check sizes of our data types, let's take ```bool``` and ```double```. Here's how to check it.
 ```c++
std::cout << "The size of bool is " << sizeof(bool) << "\n"; // The size of bool is 1
std::cout << "The size of double is " << sizeof(double) << "\n"; //The size of double is 8 byes, what a big guy!
// about std::cout and "\n"  you'll be able to find in other .md files :)
```
