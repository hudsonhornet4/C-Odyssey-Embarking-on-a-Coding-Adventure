# Templates 🩹
Templates in C++ - is the powerful feauture, that helps you to write code, which works with a lot of data types . Let's put off the theory and start with problem.
- - - -
### Problem ⚠️:
Let's say you've created a function, that helps you to return what number is greater:
```c++
#include <iostream>

//Our function
int maxNum(int a, int b){ // we choose to compare 'int' numbers
      return (a > b)? a : b; //in our language it looks like 'is A bigger than B? If yes, then return A, else B'
}



int main(){
      int a  = 10; //first argument
      int b = 15; //second argument
      std::cout << maxNum(a,b) << " is greater\n"; //Output : 15 is greater
      //Output 15 because b(15) is bigger than a(10) 
}
```
Alright, that looks good, doesn't it? 🙂 But what if you'll need to compare ```double```? That would take time and your energy. Here's finally our templates can help. 
To work with templates, we need to know how to write them:
```
template<typename [nameOfTypeName]>
[data-type] [name of function] ([arguments, optional]){
      //code
}
```
Let's make our function ```maxNum``` better.
```c++
template<typename AnyName> //i called it 'AnyName', but usually people call it just 'T'
AnyName maxNum(AnyName a, AnyName b){ 
      return (a > b)? a : b;
}
//Now here we can past and 'double' and 'float' and etc.

int main(){
      //Let's compare 'float' numbers
      float a = 15.3;
      float b = 11.89;
      //Now, to show template that we're comparing 'float' numbers, we need to write data type between brackets '<' and '>'
      std::cout << maxNum<float>(a,b) << " is greater\n"; //we pasted 'float' in brackets to show that we compare exactly our floats
      //Output: 15.3 is greater
}
```
With templates, in our ```float```, our function looks like this:
```c++
float maxNum(float a, float b){
      return (a > b)? a : b;
}
```
You should use templates, when you know that you'll need to work with different data types. Obviously, you can also work with one more typename in function, for example:
Let's create a function which calculate two ```double``` numbers and retun converted in ```int```
```c++
template<typename A, typename B>
B akaFunction(A firstNum, A secondNum){ 
      return static_cast<B>(firstNum+secondNum); //converting typename A in typename B
      //typenames can be whatever, for example i can make A as double, and B as int
}

int main(){
      akaFunction<double, int>(25.5, 15.3); // Output: 40
      //we told to compiler, that
      //typename A is 'double' and typename B is 'int'
      //and in the function, we thanks to 'static_cast' convert double result, which is 40.8 (25.5 + 15.3 = 40.8) to 'int'
}
```
So adding ```<double, int>```, our function looks like this
```c++
int akaFunction(double firstNum, double secondNum){
            return static_cast<int>(firstNum + secondNum); // result of function is 40.8, converting it to 'int' thanks to 'static_cast'
            //Returning 40
}
```

