# Function
That's an interesting part, what is a function? It is a block of code, which does a specific task, and can also return something back. You can inclue something in your function, and get magic. Let's start.
- - - - 
## Types of functions:
### Functions without a return value (aka void):
This type of functions still does a specific task, but returns nothing to you, but can change it, or print something out, or ask you something. Here's an example:
```c++
void NameOfFunction(){
  std::cout << "Hey, mate!"; //this function outputs Hey, mate! in our console.
}
```
Our function body is within our curly brackets. ```NameOfFunction``` is a name of function, and ```void``` is a data type, which means this function will return nothing, but we also can put something
in our function, you can add it within our brackets, it can be either ```int``` with called "name" or your "age".
So, we created a function, now: how can we use it? In our main block, we need to write the name of function with opened and closed brackets, since we didn't add anything in it. Here's how it looks like:
```c++
int main(int argc, char *argv[]){
  NameOfFunction(); // by writing like that, we call our function, and it will output
  //Hey, mate!
}
```
As i said, we can add something in our function, let's say: age and your name.
```c++
void printOutOurData(std::string city, int age){
  std::cout << "You live in " << city << " and you are " << age << " years old!";
}
```
Unfortunately, we cannot write ```std::cout << "You live in " + city + " and you are " + age " years old";``` like in Python, because in C++ ```+``` is an arithmetic addition, not for string concatenation.
<br>So now , when we call it again in our main block, now we supposed to add something in our called function, to make it work</br>
```c++
int main(int argc, char *argv[]){
  std::string your_city = "Houston";
  int your_age = 25;
  printOutOuData(your_city, your_age);
//You live in Houston and you are 25 years old!
}
```
The order in which variables are added must be followed to avoid errors. But you also can add variables in your functions without creating them before: 
```c++
int main(int argc, char *argv[]){
  printOutOuData("Houston", 25);
//You live in Houston and you are 25 years old!
}
```
### Function with a return value:
These functions always return something to you, whatever it is a string or number. To create a return function, we need to create it first, it has a little bit different scheme:
```c++
[data type] [name of function] ([you can include something as well){
                          //code...
}
```
For example, let's create a Cashier Function to get change:
```c++
double CashierFunction(double your_cash, double price_of_your_products){
      double change = your_money - price_of_your_products;
      return change;
}
```
```double``` in the beginning of our function means that function will return ```double``` variable/number, in our brackets we also see some ```double``` variables, which means we need to add them in our function. 
We created ```double``` variable in our function, which we will return. And inside this variable we get our change, by subtracting the amount of your products from your cash. And in the end, the function returns
our variable, which is our change. 💸 Let's call this function in our main block, because we need money!
```c++
int main(int argc, char *argv[]){
  double your_cash = 100.0;
  double your_products_price = 50.0;
  double our_change = CashierFunction(your_cash, your_products_price);
// Now, variable our_change contains 50.0.
}
```
Here we created variable ```our_change```, to give our change's number to this variable. So , now this variable contains our function's results.
But, let's have an example, What if we have not enough money? Uh-oh, let's create a function, which will check if we have enough money.
```c++
bool CheckIfEnoughMoney(double your_cash, double price_of_products){
//So, as we know, we need to use "if" and "else" in our function, let's use it.
    if(price_of_products >= your_cash) //conditions must be written in brackets{
  return false;  // since our function is bool (look at the beginning), we're supposed to return either false or true
}else{
  return true; //why we return true here?
//because there's only 3 conditions which can happen:
//either we have not enough money, and return false ( we already did it, if look up )
//or we have enough money
//or e have equal. which is good as well, in both 2 conditions we can return true
}
}
```
Now let's upgrade our CashierFunction :
```c++
double CashierFunction(double your_cash, double price_of_your_products){
      if(CheckIfEnoughMoney(your_cash, price_of_your_products){ // since our bool function returns either true or false , and we also added variables from our CashierFunction to our bool function
        //if we'll have not enough money, it will return false, if enough or equal, then true.
        double change = your_cash - price_of_your_products;
        return change;
}else{
        std::cout << "You have not enough money, sorry!\n";
        return 0.0;
}
}
```
### Inline Functions
Here's another interesting type of functions. Let's first have a look how it looks like :
```c++
inline int Square(int number){
    return number * number; //we return the result of multiplying a number on itself
}
```
We have an addition for our function! ```inline``` means, that we past our body of function, which is ```return number * number``` to our place of calling. Let's dig deeper :
```c++
inline int Square(int number){
    return number * number; //we returning the result of multiplying a number on itself
}


int main(int argc, char *argv[]){
  int number = 5;
  int result = Square(number); // since our return of function is Int, we can add the result to any Int variable
}
```
Now, the scheme looks like this :
```c++
inline int Square(int number){
    return number * number; //we returning the result of multiplying a number on itself
}


int main(int argc, char *argv[]){
  int number = 5;
  int result = number * number; // noticed something? as i said, we just use body of function
//variable result contains 25 now
}
```
Programmers usually use ```inline``` addition only for small functions. In addition, using inline functions may increase the size of the executable file because the 
function code will be duplicated at each call point. 📝
