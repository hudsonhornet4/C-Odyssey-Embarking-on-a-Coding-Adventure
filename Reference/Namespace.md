# Namespace
```namespace``` - are areas in C++ that help keep your code organized. Which can help you avoiding mistakes with names of functions, optimizing readablity . For example :
```c++
#include <iostream>
namespace Animal{
  void Sound(){
  std::cout << "*agressive racoons sounds*"; //something random, whatever.
  }
}
```
So now how can we call it? You can use the scope resolution operator ```::```. Let's call it.
```c++
#include <iostream>
namespace Animal{
  void Sound(){
  std::cout << "*agressive racoons sounds*"; //something random, whatever.
  }
}


int main(){
    Animal::Sound(); //Output: *agressive racoons sounds*
}
```
We can modify it, and add more namespace in namespace. Yes.
```c++
#include <iostream>
namespace Animal{
  namespace Cat{ //we created another namspace in 'Animal' called 'Cat'
      void Sound(){ //the name name of Animal's function
      std::cout << "Meow-Meow-Meow\n";
    }
  }
  void Sound(){
  std::cout << "*agressive racoons sounds*"; //something random, whatever.
  }
}
//to clal it we still can use '::', but now a little bit more, since here's ANOTHER namespace
int main(){
//lets define old function first
    Animal::Sound(); //Output: *agressive racoons sounds*
//now let's put our cat's sounds down here
    Animal::Cat::Sound(); // Output: Meow-Meow-Meow

}
```
You also can get variables from ```namespace```s. For example:
```c++
namespace Boo{
std::string boo {"👻Boo!"};
}
//getting things from namespace is the same as getting functions
int main{
  std::cout << Boo::boo << "\n";
  std::cout << "A-A-A-A-A!!\n"; 
}
```

## ```using namespace std```
Every C++ programmer already heard that including ```using namespace std``` is a bad practice, and that's better to use ```using std::cout``` or ```using std::cin```, to make it look like that:
```c++
using std::cout; 

int main(){
  cout << "Hello World!\n";
]
```
Why? Let's imagine you included two libraries in your code:
```c++
using namespace std;
using namespace dtc; //I made this up a few seconds ago
```
as we know, STD library has ```cout```, which makes it easier to write. But what if ```using namespace dtc``` has ```cout``` too?
```c++
using namespace std;
using namespace dtc;
int main(){
  cout << "Hello World!\n";
//who's 'cout' are you using from? from 'std' or 'dtc'?
}
```
So you'll have to fix this, and it will take time. But that's bette to just add some symbols.. isn't it?
```c++
int main(){
  std::cout << "Hello World from std!\n"; // that's called from 'std'
  dtc::cout << "Hello from dtc!\n"; // that's called from dtc
}
```
### ```typedef```
Or you can use ```typedef```, which will give your things a different name. For example:
```c++
typedef std::cout stcout; //now our 'std::cout' name is 'stcout'
typedef dtc::cout dtcout; //now our 'dtc::cout' name is 'dtcout'

int main(){
    stcout << "Hello World from std!\n"; 
    dtcout << "Hello from dtc!\n"; 
}

```
