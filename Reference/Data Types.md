# Data Types in C++ 👩‍💻👨‍💻
There's a lot of data types in C++ which you should know. But we need to define them correct first. Let's see how we can do that :
```c++
[data type] [name] = [value];
[data type] [name] {value};
[data type] [name] (value);
```
But better use first type. 🚀
- - - - 
## Primitive Data Types:
### Int 🧮
The ```int``` data type in C++ is used to store integer values. It can hold both positive and negative whole numbers. The size of the int data type is typically 4 bytes, but it can vary depending on the compiler and the computer architecture.

Here are some key points about the int data type:

- 🎯 **Range**: The range of values that can be stored in an int depends on the number of bytes allocated for it. For a 4-byte int, the range is approximately -2 billion to 2 billion (-2.147.483.648 to 2.147.483.647).
- 📦 **Default Initialization**: If you declare an int variable without assigning a value, it will be initialized to 0 by default.
- 🔍 **Arithmetic Operations**: You can perform various arithmetic operations on int variables, such as addition, subtraction, multiplication, and division.
- 🤒 **Overflow**: If the result of an arithmetic operation exceeds the range of the int data type, it will cause an overflow, resulting in undefined behavior.
  For example, since our positive limit is 2.147.483.647, **we cannot reach more than it.**
  ```c++
  int ourMaximumLimit = 2147483647; //we created an integer with name "ourMaximumLimit" with maximum value
  int overMaximum = ourMaximumLimit + 1; // here's we created another integer with value from "ourMaximumLimit" but in 1 more.
  std::cout << "ourMaximumLimit = " << ourMaximumValue << "\n";
  std::cout << "overMaximum = " << ourMaximumValue << "\n";
  ```
  As a result we'll see something like that:
  ```
  ourMaximumValue = 2147483647
  overMaximum = -2147483648;
  ```
  Weird, innit? 🤔
  <br>⚠️The reason overflow happens is **due to the finite representation of numbers in computer memory**. In binary representation, integers are stored using a fixed number of bits. For example, a 4-byte int can store values from -2,147,483,648 to 2,147,483,647. When you perform an arithmetic operation that results in a value outside this range, the representation of the number exceeds the available bits, causing an overflow. </br>

- **Modifiers**: You can use modifiers like short, long, and long long to specify different sizes of the int data type. For example, short int is a 2-byte integer, long int is a 4-byte integer, and long long int is an 8-byte integer.
```c++
int a = 5; // variable "a" has a value 5
int b{25}; // variable "b" has a value 25
int c(-19); //variable "c" has a value -19
```
### Float 🌊
The ```float``` data type in C++ is used to store single-precision floating-point numbers. It is used to represent decimal numbers with a smaller range and less precision compared to the ```double``` data type.You should use ```double``` when you need **higher precision and accuracy**, and **memory usage is not a concern**. Use ```float``` when memory efficiency is important, and you **can tolerate slightly lower precision.**
Here are some key points about the float data type:

- **Range**: The range of values that can be stored in a float is approximately ±1.17549e-38 to ±3.40282e+38. It can represent both positive and negative numbers.
- **Size**: The float data type typically occupies **4 bytes** (32 bits) of memory.
- **Precision**: The precision of a float is approximately 6 decimal places. It means that a float can accurately represent decimal numbers up to 6 digits.
- **Default** Initialization: If you declare a float variable without assigning a value, it will be initialized to 0.0 by default.
- **Arithmetic Operations**: You can perform various arithmetic operations on float variables, such as addition, subtraction, multiplication, and division.
- **Floating-Point Errors**: Due to the limited precision of the float data type, there can be rounding errors and inaccuracies in calculations involving float values. It's important to be aware of these limitations when working with float variables.
<br>🎯 Additionally, you can write float numbers with ```f``` in the end of numbers, which will show that your number is 100% float.</br>
```c++
float q {25.5};
float w = 15.1f; //the variable is 100% float
float e = 15; //ERROR, to fix this -> add decimal point and either 0 or any other number
```
### Double 🌊🌊
The double data type in C++ is used to store double-precision floating-point numbers. It provides higher precision and a larger range compared to the float data type.

Here are some key points about the double data type:

- **Range**: The range of values that can be stored in a double is approximately ±2.22507e-308 to ±1.79769e+308. It can represent both positive and negative numbers.
- **Size**: The double data type typically occupies 8 bytes (64 bits) of memory, which is twice the size of a float.
- **Precision**: The precision of a double is approximately 15 decimal places. It can accurately represent decimal numbers with greater precision compared to float.
- **Default Initialization**: If you declare a double variable without assigning a value, it will be initialized to 0.0 by default.
- **Arithmetic Operations**: You can perform various arithmetic operations on double variables, such as addition, subtraction, multiplication, and division.
- **Floating-Point Errors**: While double provides higher precision, it is still subject to floating-point errors due to the limitations of representing real numbers in binary format. It's important to be aware of these limitations when working with double variables.
```c++
double a = 5.1;
double b {11.2};
double c = 12;
```

### Char 🎵
The ```char``` data type in C++ is used to represent individual characters. It is used to store single characters such as letters, digits, and special symbols.

Here are some key points about the char data type:

- **Size**: The char data type typically occupies **1 byte** (8 bits) of memory.
- **Range**: The range of values that can be stored in a char is from -128 to 127 or 0 to 255, depending on whether it is ```signed``` or ```unsigned```. By default, char is signed, but you can explicitly specify it as unsigned using the unsigned char type.
- **Character Encoding**: The char data type uses the ASCII (American Standard Code for Information Interchange) character encoding by default. Each character is represented by a unique numeric value.
- **Character Literals**: Characters can be represented using single quotes ('). For example, 'A', 'b', '1', '@' are all valid char literals.
- **Escape Sequences**: Certain characters have special meanings and cannot be directly represented using single quotes. In such cases, you can use escape sequences, such as ```\n``` for a newline character or ```\t``` for a tab character.
- **String Literals**: A sequence of characters enclosed in double quotes (") is called a string literal. It is represented as an array of char values, with an additional null character ('\0') at the end to indicate the end of the string.
```c++
char a = 'i';
char b = '#';
char c = '-';
```
But additionally to symbols, you also can represent and manipulate ```strings``` aka text. For example:
```c++
char[] exampleName1= "Bob";
char[] exampleName2 = "Hello, that's a string!";
```
Some of you can say that it's better to write ```std::string``` , and you're right. Using ```std::string``` offers a higher level of abstraction, safety, convenience, and performance optimization compared to manually managing char arrays. It simplifies string manipulation, reduces the risk of errors, and improves code readability and maintainability.

But, exist situations where using ```char[]``` is necessary or more appropriate, such as when working with legacy code, interacting with **C-style APIs**, or dealing with low-level memory operations. In such cases, caution should be exercised to ensure proper memory management and avoid potential vulnerabilities.


### Bool ✔️❌
The ```bool``` data type in C++ is used to represent boolean values, which can have one of two possible states: true or false. Boolean values are commonly used in programming for logical operations, decision-making, and conditional statements.

Here are some key points about the bool data type:

- **Size**: The bool data type typically occupies 1 byte (8 bits) of memory.
- **Values**: The bool data type can only have two possible values: true or false. true represents a logical true value, while false represents a logical false value.
- **Logical Operators**: Boolean values can be combined using logical operators such as && (logical AND), || (logical OR), and ! (logical NOT). These operators allow you to perform logical operations and evaluate conditions based on boolean values.
- **Comparison Operators**: Boolean values can also be compared using comparison operators such as == (equality), != (inequality), < (less than), > (greater than), <= (less than or equal to), and >= (greater than or equal to). These operators return boolean values as the result of the comparison.
- **Conditional Statements**: Boolean values are commonly used in conditional statements such as if statements and while loops to control the flow of execution based on certain conditions.
- **Default Initialization**: If you declare a bool variable without assigning a value, it will be initialized to false by default.
```c++
bool a = true;
bool b = false;
std::cout << "a = " << a << '\n';
std::cout << "b = " << b;  
```
If we will print it out, we'll have something like this:
```c++
a = 1
b = 0
```
From Computer Science lessons we know that true means **1**, and false means **0**, but.. what if we want to print out ```true``` and ```false``` instead of numbers? To do it we need to write:
```c++
std::cout << boolalpha; //enabled to print false and true
bool a = true;
bool b = false;
std::cout << "a = " << a << '\n';
std::cout << "b = " << b;
std::cout << noboolalpha; //disabled to print false and true
```
🎉 And we will have false and true instead of numbers, yay:
```c++
a = true
b = false
```

