# Constants
What is constants? That's an additions to our variables, constants shows that value of variable will not be changed. Let's start.
- - - - 
First, to create constant variable we need to add ```const``` before data type of our variable. It can look like this:
```c++
const int speed_of_light = 299792458; // "const" before variable means that we cannot change the value of this variable. aka speed_of_light
int speed_of_light += 1; //ERROR 
```
But you should always remember that const variables supposed to be initialized.
```c++
const int a; //ERROR, you must give a value
const double b = 15.8; //CORRECT
```
You also can initlize const variable's value from other variable's values, for example :
```c++
int speed_of_sound = 343; // non-constant variable
const int SpeedOfSound {speed_ofsound}; //we initialized const variable with using non-constant value
speed_of_sound = 344; // we can change it, because this variable is not constant
```
Logically, isn't it? 🤔
### Using const in Return Functions
<br>Additionally, you should avoid using ```const``` in functions which return something.</br>
```c++
const int ResturnSomething(){
    return 15;
}
```
Reasons : 

- 👀 **Redundancy**: When you return a value by value, the returned value is already a temporary copy of the original object.
Adding const to the return type does not provide any extra guarantees or immutability. It only adds unnecessary complexity to the code without any practical benefit.

- ⚠️ **Inconsistency**: Most C++ codebases and libraries do not use const in the return type when returning by value.
By following this convention, your code will be more consistent with common practices, making it easier for other developers to understand and maintain.

- 📖 **Readability**: Adding const to the return type can make the code harder to read and understand, especially for those who are not familiar with this usage.
It may give the impression that the returned value is somehow more restricted or immutable, which is not the case when returning by value.

- 🤔 **Compatibility**: Using const in the return type when returning by value can potentially cause compatibility issues with older compilers or libraries that do not support this usage.
By avoiding const in this context, you ensure better compatibility across different environments.
