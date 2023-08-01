# Smart Pointers
C++ is like a school, there a raw and average pointers and smart pointers. Smart pointers is a powerful feauture of C++ Standard Library,
they're like an ordinary pointer, but also can manage allocation and deallocation of the objects. Forget about your ```new``` and ```delete```, they'll do it themselves.
With them you don't have to worry about memory leakage and other problems. There are different smart pointers:

### - 1️⃣ ```std::unique_ptr```
### -  2️⃣ ```std::shared_ptr```
### -   3️⃣ ```std::weak_ptr```
### - 😖 ```auto_ptr``` - this guy was removed in ```C++17```, so we won't talk about it. 🌹
- - - -
⚠️ Before using smart pointers, we must include ```<memory>``` in our file
## ```unique_ptr```
```unique_ptr``` is a smart pointer provided by C++11 to prevent memory leaks. 
It's an object that wraps around a raw pointer and is responsible for its lifetime. This means that when this object is destructed, 
it deletes the associated raw pointer. unique_ptr has its ```->``` and ```*``` operators overloaded, so it can be used similarly to a normal pointer.

A ```unique_ptr``` is a greedy guy 😥, it does not share its pointer. It cant be copied to another ```unique_ptr```, passed by value to a function, or used in any C++ Standard Library algorithm that requires copies to be made. 
A ```unique_ptr``` can only be moved, which means that the ownership of the memory resource is transferred to another ```unique_ptr``` and the original ```unique_ptr``` no longer owns it.

### When and why to use a unique pointer?
Unique pointers are useful in situations where you want to have exclusive ownership of a resource in a specific area of code. 
They are especially useful **for preventing memory leaks** and simplifying resource management 

<br>Here are some examples of situations in which unique pointers can be useful:</br>
- **Interacting with a C or C-like library**: You may need to use "raw" pointers that you release at the very last moment. You can get a _"raw"_ pointer from a unique pointer using the operation.
- **Improving compilation speed**: Unique pointers can be useful when separating compilation.
- **Resource Management**: Unique pointers can help avoid memory leaks by automatically freeing resources when they go out of scope.
For example :
```c++
#include <memory>

int main() {
    std::unique_ptr<int> ptr(new int(5)); // Creating a unique pointer at 'int'
    *ptr = 10; // Changing the value that the unique pointer points at
    return 0;
} // The pointer will be automatically deleted here, freeing up the resource
```
You can also use the ```reset``` method to release resources to the end of the scope:
```c++
#include <memory>

int main() {
    std::unique_ptr<int> ptr(new int(5)); // Creating a unique pointer at 'int'
    ptr.reset(); // The resource will be released here
    return 0;
} // Nothing will happen here since the resource has already been released
```
You also can create a unique pointer, using ```make_unique```, for example:
```c++
std::unique_ptr<int> ptr (new int);
```
### How to give an access to value of ```unique_ptr```?
```unique_ptr``` in C++, it does not divide its pointer. It cant be copied to another ```unique_ptr```, passed by value to a function, or used in any C++ Standard Library algorithm that requires creating copies. 
It can only be moved. That means that ownership of the memory resource is transferred to another ```unique_ptr```, and the original ```unique_ptr``` is no longer its owner.

<br>```unique_ptr```s are like a greedy kitty 😾, when you give a plate of food 🥫, the greedy kitty comes and eats all, then wants eat others</br>
Let's visualise it:
```c++
#include <iostream>
#include <memory>

class Food { 
public:
    Food(const std::string& name) : name_(name) { // with 'name_(name)' we gave a value of constructor to 'name_' in private
        std::cout << "Food: " << name_ << " created.\n";
    }

    ~Food() {
        std::cout << "Food: " << name_ << " is eaten.\n";
    }

    const std::string& name() const { return name_; }

private:
    std::string name_;
};

class Kitty {
public:
    Kitty(const std::string& name) : name_(name) {}

    void giveFood(std::unique_ptr<Food> food) {
        std::cout << "Giving " << food->name() << " to " << name_ << ".\n";
        food_ = std::move(food);
    }

    void eatFood() {
        if (food_) {
            std::cout << name_ << " eats " << food_->name() << ".\n";
            food_.reset();
        } else {
            std::cout << name_ << " has no food to eat.\n";
        }
    }

private:
    std::string name_;
    std::unique_ptr<Food> food_;
};

int main() {
    Kitty kitty("Whiskers");
    // Giving kitty one food
    kitty.giveFood(std::make_unique<Food>("fish"));
    // Kitty eats the food
    kitty.eatFood();
    // Uh-oh, no food now.
    kitty.eatFood();
    //alas, mate.

    return 0;
}

```

## ```shared_ptr```
A ```shared_pt```r is a smart pointer in C++ that allows you to share ownership of a dynamically allocated object with other ```shared_ptr``` instances. 
Object may have a lot of ```shared_ptr```, but when last ```shared_ptr``` will be deleted - the Object will be deleted as well.
<br>Let's visualise ```shared_ptr``` with a lof of kitties which shares one food with each other, and when kitties are gone, food is gone as well:</br>
```c++
#include <iostream>
#include <memory>

class Food {
public:
    Food(const std::string& name) : name_(name) {
        std::cout << "Food: " << name_ << " created.\n";
    }

    ~Food() {
        std::cout << "Food: " << name_ << " is eaten.\n";
    }

    const std::string& name() const { return name_; }

private:
    std::string name_; // to get a name of food
};

class Kitty {
public:
    Kitty(const std::string& name) : name_(name) {}

    void giveFood(std::shared_ptr<Food> food) { //⚠️ we use shared_ptr here
        std::cout << "Giving " << food->name() << " to " << name_ << ".\n";
        food_ = food;
    }

private:
    std::string name_;
    std::shared_ptr<Food> food_;
};

int main() {
    auto food = std::make_shared<Food>("Best Fish"); // create a food

    auto kitty1 = std::make_shared<Kitty>("Kit-Kat"); // that's our first cat
    kitty1->giveFood(food);    // we gave him a food which we created 

    auto kitty2 = std::make_shared<Kitty>("Mr. Mistoffelees"); // that's our second cat
    kitty2->giveFood(food);   // we have him the same food which we gave to Kit-Kat

    // When the kitties are gone, the food will be eaten
    kitty1.reset();
    kitty2.reset();

    return 0;
}
```
![shared_ptr](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/9cc11d6a-b08f-49b7-9f58-d1fa7215dc85)

## ```weak_ptr```
A weak_ptr in C++ is a smart pointer that does not prevent the object it points to from being deleted. 
This means that the ```weak_ptr``` can "observe" the object, but it cannot "own" the object. For example:
<br>Imagine a party, a lot of people are hanging out:</br>
- **Party** - is an Object, what ```shared_ptr``` pointing at
- **People** - are ```shared_ptr```, they use Party, eat food, hang out and etc.
- **Man, that no one notice** - is a ```weak_ptr```, he stays in the corner of party,  but still hanging out and eating food
```c++
#include <iostream>
#include <memory>

class Party {
public:
    Party() {
        std::cout << "Party created.\n";
    }

    ~Party() {
        std::cout << "Party is ended.\n";
    }

    void useFood() {
        std::cout << "Food is being used at the party.\n";
    }
};

int main() {
    std::shared_ptr<Party> partyPtr = std::make_shared<Party>(); // creating a party

    std::weak_ptr<Party> weakPartyPtr = partyPtr; //making our guy do what other's do

    partyPtr->useFood(); //people (shared_ptr) using food

    if (auto sharedPartyPtr = weakPartyPtr.lock()) { //checking if shared_ptrs(people) are exist (still at the party)
        sharedPartyPtr->useFood(); //if object shared_ptrs exists, then our shy guy (weak_ptr) eating food
    } else {
        std::cout << "The party is over.\n"; //if shared_ptr do not exist - then party is over
    }

    partyPtr.reset();

    if (auto sharedPartyPtr = weakPartyPtr.lock()) {
        sharedPartyPtr->useFood();
    } else {
        std::cout << "The party is over.\n";
    }

    return 0;
}
```
```
Party created.
Food is being used at the party. //by shared_ptrs (people)
Food is being used at the party. //by our shy guy (weak_ptr)
Party is ended.
The party is over.
```
![weak_ptr](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/baa9df66-525c-49f7-a8bc-33f03640329d)
### When to use ```weak_ptr```?
- When you need to access an object that is owned by another object.
- When you need to break a circular reference.
- When you need to implement an observer pattern.
- - - -
### ```expired()``` in weak_ptrs
The ```expired()``` function in C++ checks if a ```weak_ptr``` is still valid. 
A ```weak_ptr``` is valid if the object that it points to is still alive. If the object is no longer alive, the ```weak_ptr``` **is expired**.
For example: 
```c++
#include <iostream>
#include <memory>

using namespace std;

int main() {
  // Create an object and point a weak_ptr to it
  int* p = new int(10);
  weak_ptr<int> wptr = p;

  // Check if the object is still alive
  if (wptr.expired()) {
    cout << "*ptr is no longer alive\n";
  } else {
    cout << "*ptr is still alive\n";
  }

  // Delete the object
  delete p;

  // Check if the object is still alive
  if (wptr.expired()) { //checking
    cout << "*ptr is no longer alive\n";
  } else {
    cout << "*ptr is still alive\n";
  }
}
```

```
*ptr is still alive
*ptr is no longer alive
```
