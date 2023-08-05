# Vectors
Vectors in C++ are containers, which stores elements inside. Whatever they are : ```char```, ```int```, ```double```. That's like a dynamic arrays with an ability to resize itself when you insert an element in. 
### <br>📑 To work with elements, you need to include ```<vector>```</br>
For example :
```c++
#include <vector>


int main(){
      std::vector<int> Our_Vector = {5,2,5,8,1,6};
 //we created 'int'↑ vector, which obviously contains 'int' numbers
}
```
![vector1](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/9e05f5fb-c46b-4d91-885e-a0b07f2e41f8)

As you can see, we can see that size starts from 1, and index from 0. An index refers to the position or location of an element within the vector.
Let's start our experiments with this vector.
- - - -
## ```begin()``` and ```end()```:
Iterator ```begin()``` points at first object in our vector, and ```end()``` at last object, for example : 
```c++
int main(){
      std::vector<int> Our_Vector = {5,2,5,8,1,6};
      std::for_each(Our_Vector.begin(), Our_Vector.end(), [](const int a){std::cout << a << " "; // Output: 5 2 5 8 1 6
      //starting from the beginning ↑ and  ↑ finishing in the end
}
```
[Lambda](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/blob/Default/Reference/Lambda.md) ```[](const int a){std::cout << a << " ";``` helps us print out the vector, you can read about it here. And ```std::for_each``` is a standard library algorithm that allows you to interact with each element of a vector.
![vector2](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/1e6f0aad-589a-4736-871e-6c499cc139eb)
## ```empty()```
```empty()``` is a function of vector which returns ```false```(0) if a vector is not empty, and ```true```(1) if it's empty. 
```c++
int main(){
      std::vector<int> Our_Vector;
      //Our Vector has no elements
      std::cout << std::boolapha; //helps us return 'true' and 'false' instead of '1' and '0'
      std::cout << "Our_Vector has no elements, so it's " << Our_Vector.empty() << "\n"; // Output: Our_Vector has no elements, so it's true
      Our_Vector.push_back(5); //adding an element '5' from back of vector
      std::cout << "Our_Vector has elements now, so it's " << Our_Vector.empty() << "\n"; // Output: Our_Vector has elements now, so it's false
}
```
## ```size()```
```size()``` returns the number of elements in our vector. For example:
```c++
int main(){
      std::vector<int> Our_Vector = {5,2,5,8,1,6};
      std::cout << "The number of elements in our vector is " << Our_Vector.size(); // Output: The number of elements in our vector is 6
}
```
![vector_size](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/32b72197-2a35-40f1-95c1-7af807c587ac)
## ```reseve()```
```reserve()``` allocates memory for a vector in advance, without actually adding any elements to it. For example:
```c++
int main(){
      std::vector<int> Our_Vector;
      //Our Vector has no elements now
      Our_Vector.reserve(5);
      std::cout << "Size of our vector is " << Our_Vector.size(); //Size of our vector is 5
}
```
![vector_reseve](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/a9c84fc0-1fe3-4ede-9b8f-ea491538785e)
## ```push_back()```
```push_back()``` adds an element in the end of vector. For example :
```c++
int main(){
      std::vector<int> Our_Vector = {5,2,5,8,1,6};
      Our_Vector.push_back(9);//adding '9' right after our '6' in the end
      for(int i : Our_Vector)
      {
          std::cout << i << " "; //Output: 5 2 5 8 1 6 9
                                         //our element ↑
      }
      
}
```
![vector_push_back](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/7c4335b5-559f-4cdc-b3eb-6ee6d8553a3d)
## ```pop_back()```
```pop_back()``` deletes an element in the end of vector, yes. For example:
```c++
int main(){
      std::vector<int> Our_Vector = {5,2,5,8,1,6};
      Our_Vector.pop_back(); removing last element in vector 'Out_Vector'
      for(int i : Our_Vector)
      {
          std::cout << i << " "; //Output: 5 2 5 8 1 
                                        //no '6' now ↑
      }
      
}
```
![vector pop_back](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/134860ab-d0f8-4e84-b348-1753dcf3e48e)

