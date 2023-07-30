# Pointers
Pointers are variables that store the memory address of another variable. 
They allow us to indirectly access and manipulate the value of a variable by referring to its memory address.
Pointers are commonly used in programming languages like C and C++.
### Pointers are useful for several reasons:
- Dynamic memory allocation: Pointers allow us to allocate memory dynamically at runtime, which can be useful when we don't know the exact amount of memory needed in advance.

- **Efficient memory usage**: Pointers can help optimize memory usage by allowing us to pass memory addresses instead of copying large data structures.
- **Manipulating data structures**: Pointers enable us to create complex data structures like linked lists, trees, and graphs, where each element points to another element.
- **Function parameter passing**: Pointers can be used to pass variables by reference to functions, allowing the function to modify the original variable.
Here's an example to illustrate the use of pointers in C:
```c++
#include <iostream>

int main() {
    int number = 10;
    int *ptr;

    ptr = &num; // Assign the address of num to ptr

    std::cout << "Num's value is " << number "\n";
    std::cout << "Adress of num is " << &number << "\n";
    std::cout << "ptr's value is " << ptr << "\n";
    std::cout << "Value, which ptr pointing at is " << *ptr << "\n";

    *ptr = 20; // Change the value of num through ptr

    std::cout << "Now, num's value is " << num << "\n";

    return 0;
}
```
```
Num's value is 10
Adress of num is [num's adress]
ptr's value is [num's adress]
Value, which ptr pointing at is 10
Now, num's value is 20
```
Let's create another example, let's imagine you gave your disk with game to your friend, but it didn't give you back, well, you can get it with pointers.
Let's have a look:
```c++
int main(){
  bool John = false;
  bool Bob = false;
  bool Kevin = true; // but we won't touch Kevin, he's already true man.
}
```
We created 3 friends, which will supposed to give us our game back. 
```c++

void takeTheGame(bool *our_friend ){ //we created a pointer, to point at particular friend, without creating a copy
  our_friend = true; //kinda means that particular friend gave our game back, just switch from :
//false - didn't give back
//true - gave back.
}

int main(){
  bool John = false;
  bool Bob = false;
  bool Kevin = true;
//now let's get them
  takeTheGame(&John); // we writ "&" before the name of variable to point at ADRESS of variable, not the value
  takeTheGame(&Bob);  //with this we set value of our friends to true
  takeTheGame(&Kevin);
  std::cout << "Did John give us our game back : " << John << "\n" // we write without "&" because we dont need their adress, we need just the value
  std::cout << "Did Bob give us our game back : " << Bob << "\n"
  std::cout << "Did Kevin give us our game back : " << Kevin << "\n" //Sorry Kevin
}
```
```
Did John give us our game back : 1
Did Bob give us our game back : 1
Did Kevin give us our game back : 1 
```
As we see, everything is true, we got our game back. But what if we didn't write "*" before name "our_friend" in our function ```takeTheGame```? It would create a copy,
what it means? Simply, we would take our game from not our John, Kevin and Bob, that would be just strangers, so we kinda robbed them. But our original, friends Bob, John and Kevin 
still have our games. Let's demonstrate it :
```c++
void takeTheGame(bool our_friend ){ //now without "*" we create a copy and change it, without changing ORIGINAL
  our_friend = true; 
}

int main(){
  bool John = false;
  bool Bob = false;
  bool Kevin = true;
//now let's get them
  takeTheGame(John); // without "&" it means that this is new created variable (copy) has another adress
  takeTheGame(Bob);  
  takeTheGame(Kevin);
  std::cout << "Did John give us our game back : " << John << "\n" 
  std::cout << "Did Bob give us our game back : " << Bob << "\n"
  std::cout << "Did Kevin give us our game back : " << Kevin << "\n" 
}
```
```
Did John give us our game back : 0
Did Bob give us our game back : 0
Did Kevin give us our game back : 1 
```
Oh no, we have our games.. but friends still didn't give our game back, then what did we do? We created another John, Bob and Kevin and took their game.
<br>You did a crime, Jimmy. 🚔👮</br> 
But Kevin is true because he was already true, before creating a copy and changing it.
- Since the ```takeTheGame``` function works with copies of the variables, modifying the friend parameter inside the function does not affect the original variables in the ```main``` function.
- The original values of John, Bob, and Kevin remain unchanged, so the output shows the initial values of ```false``` for John and Bob, and ```true``` for Kevin.
# When to use pointers?
Pointers are a way of storing the addresses of other variables in C++. They can do many things, such as:

- 📝**Make memory access and manipulation faster and easier**: Pointers let you go straight to the memory locations you want, which can save time and code. They are very handy for working with strings, trees, arrays, structures, and functions. 
- 🛠️ **Create and delete memory on the fly**: Pointers can help you allocate and free memory when you need it. This means that you can use memory as you please, without wasting any resources.
- 📊 **Work with data structures**: Pointers are often used in data structures like linked lists and binary trees. They make it easy to change and move around the elements by storing their addresses.
- 🧮 **Pass large data structures to functions**: Pointers can be used as function arguments to avoid copying a lot of data. By passing pointers by reference, you can change the data directly in memory, which can be faster.
- 🧊**Access objects of derived classes through base class pointers**: In C++, a pointer to a base class can access the object of a derived class. This allows for different types of objects to behave differently and is a key idea in object-oriented programming.
- 💻**Do system-level programming**: Pointers are useful in system-level programming where memory addresses matter, such as working with hardware or low-level operations.
- 🔧 **Return multiple values from a function**: Pointers can be used to return more than one value from a function. By passing pointers as function arguments, the function can modify the values stored at those addresses 

And in the end.. be careful with pointers. 🤫
