# Standard Template Library (STL) 📚
The Standard Template Library (STL) is a C++ library that provides a collection of data structures, algorithms, and utility functions.
STL aims to provide components that can be reused and efficient for common programming tasks. Let's look at some of them. Some algorithms from STL i wrote in [Vectors.md](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/blob/Default/Reference/Vectors.md)
- - - -
### ```std::find```
```std::find``` help us to find an element in range we write. For example :
```c++
#include <iostream>
#include <vector>

int main(){
      std::vector<int> our_Vector = {5,2,1,6,3};     //we created a vector
      auto findOurElement = std::find(ourVector.begin(), our_Vector.end(), 5);
//                    where we start to search ↑ and where we end  ↑ | '5' is ↑ what we want to find in our vector
      if(findOurElement != our_Vector.end(){
//if 'findOurElement' will find our '5', it will point at our index of this number, otherwise it will point at the end
//so we check, if 'findOurElement' does not point at the end, then it means 'findOurElement' found our number
            std::cout << "The number was found!\n";
      }else{
              //if 'findOurElement' points at the end (our_Vector.end()), it means it didnt find our element
              std::cout << "The number was not found.\n";
        }
}
```
### ```std::binary_search```
That's like a ```std::find``` , so what's the difference? 🤔
<br>📑```std::find``` works with unsorted array, ```std::binary_search``` does not. 
That means you will not be able to use ```std::binary_search``` with array like ```[6,4,2,7,4]```</br>
```c++
#include <iostream>
#include <vector>

int main(){
      std::vector<int> our_SortedVector = {1,2,6,8,10}; //the vector is sorted
      int numberToFind = 8;
      auto foundIt = std::find(ourVector.begin(), our_Vector.end(), numberToFind, [&our_SortedVector](size_t ind, int valueToCompare) -> bool{return v[ind] < valueToCompare;});
//                                                                    ↑'8'   getting adress of ↑ our array           this lambda function ↑ returns 1 or 0
      if(foundIt){
            std::cout << "The number was found!\n";
      }else{
              std::cout << "The number was not found.\n";
        }
}
```

🔖 About ```[&our_SortedVector](size_t ind, int valueToCompare) -> bool{return v[ind] < valueToCompare;```
- ```&our_SortedVector``` means we work with original adress of ```our_SortedVector```, not creating a copy
- ```size_t ind``` represents each element in our vector ```our_SortedVector```. I used ```size_t``` because that's an unsigned type, which cannot be negative. We obviously can use ```unsigned int``` because that's ```size_t```'s synonymous,
    but ```size_t``` is usually used to to represent sizes and indices.
-  ```int valueToCompare``` represents the value we want to compare against.
-  ```-> bool``` means we're going to return exactly ```bool``` type.
### ```std::lower_bound``` and ```std::upper_bound```
```std::lower_bound``` returns the index of an element that we want to find that no less than our element, and ```std::upper_bound``` returns the index of the first element in an array that is larger than our element that we want to find.
```c++
//------------------------------------------------lower_bound------------------------------------------------
#include <iostream>
#include <vector>
#include <algorithm>   //don't forget about this

int main() {
    std::vector<int> our_Vector = {1, 2, 2, 4, 4, 7, 8, 9, 9,10};
// we want to find '4' so lower is          ↑
    int toFind = 4;                          
    auto lowerToFind = std::lower_bound(our_Vector.begin(), our_Vector.end(), toFind);
    //if it wont find, as usual it will point at last element of vector (our_Vector.end())
    if(lowerToFind != our_Vector.end()){
      std::cout << "Lower bound of array at index " << std::distance(our_Vector.begin(), lowerToFind) << "\n"; //Output: Lower bound of array at index 3
}
    else{
          std::cout << "The number was not found\n";
    }
}
```
```c++
//------------------------------------------------upper_bound------------------------------------------------
#include <iostream>
#include <vector>
#include <algorithm>   

int main() {
    std::vector<int> our_Vector = {1, 2, 2, 4, 4, 7, 8, 9, 9, 10};
// we want to find '9' so upper is                             ↑
    int toFind = 9;                          
    auto upperToFind = std::upper_bound(our_Vector.begin(), our_Vector.end(), toFind);
    if(upperToFind != our_Vector.end()){
      std::cout << "Upper bound of array at index " << std::distance(our_Vector.begin(), lowerToFind) << "\n"; //Ouput: Upper bound of array at index 9
}
    else{
          std::cout << "The number was not found\n";
    }
}
```
### ```std::erase```
```std::erase``` helps you to remove elements from a container based on their value.
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector = {1, 2, 3, 4, 5, 2, 6, 7};

    // Remove all '2' in 'Our_Vector'
    std::erase(Our_Vector, 2);

    // Print the updated vector
    for (int objects : Our_Vector) {
        std::cout << num << " ";
    }
}

```
### ```std::count```
```std::count``` helps you to count the number of instances of a specific value.
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector = {5, 1, 3, 2, 4, 2, 5, 2};
//                                 ↑                 ↑
    // Count how many '5' in 'Our_Vector'
    int count = std::count(Our_Vector.begin(), Our_Vector.end(), 2);

    std::cout << "The number of '5' is " << count << "\n"; //Output: The number of '5' is 2
}
```
### ```std::swap```
```std::swap```  helps you to swap the values of two objects or variables.
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector1 = {5, 2, 1}; //fist vector with elements 5 2 1
    std::vector<int> Our_Vector2 = {8, 10, 4}; // second vector with elements 8 10 4

    // Swap the elements of 'Our_Vector1' and 'Our_Vector2'
    std::swap(Our_Vector1, Our_Vector2);

    // Let's print them out
    for (int num : Our_Vector1) {
        std::cout << num << " ";
    }
    std::cout << "---------------------------------------";

    for (int num : Our_Vector2) {
        std::cout << num << " ";
    }

}
```
```
8 10 4 //Our_Vector1 now
---------------------------------------
5 2 1  //Our_Vector2 now
```
### ```std::sort```
```std::sort``` helps you to sort elements in your vector.
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector = {5, 2, 1, 6, 3};

    // ↓ sort 'Our_Vector' in ascending order
    std::sort(Our_Vector.begin(), Our_Vector.end());

    for (int num : Our_Vector) {
        std::cout << num << " ";
    }
}

```
```
1 2 3 5 6
```
### ```std::reverse```
```std::reverse``` actually reverse the order of elements in your given range, so if you had 1 2 3, it will be 3 2 1
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector = {6, 2, 1, 7, 2};

    // Reverse the elements in 'Our_Vector'
    std::reverse(Our_Vector.begin(), Our_Vector.end());

    // Print the reversed vector
    for (int num : Our_Vector) {
        std::cout << num << " ";
    }
}

```
```
2 7 1 2 6
```
### ```std::distance```
```std::distance``` helps you to calculate number of elements between your range.
```c++
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> Our_Vector = {1, 6, 2, 9, 12, 2};
    int distanceBetween = std::distance(Our_Vector.begin(), Our_Vector.end());

    // Print the distance
    std::cout << "Distance between first and last elements is " << distanceBetween << "\n";
}

```
```
Distance between first and last elements is 6
```

### ```std::move```
```std::move``` helps you to move elements from one vector(array) to another array, but fist array will be empty after this.
```c++
#include <iostream>
#include <vector>
#include <utility>      //DON"T FORGET THIS FOR std::move

int main() {
    std::vector<int> Vector1 = {6, 1, 2, 66, 3};

    // Use std::move to transfer the content of 'Vector1' to 'Vector2'
    std::vector<int> Vector2 = std::move(Vector1); // in brackets we write from WHAT vector we're going to steal elements
//                                 ↑ taking elements from 'Vector1' to 'Vector2'

    std::cout << "Vector1 size after move is " << Vector1.size() << "\n";

    //print out elements in  'Vector2'
    for (int num : Vector2) {
        std::cout << num << " ";
    }
}
```
```
Vector1 size after move is 0 //because it's empty after moving
6 1 2 66 3 //Vector2 elements 
```
### ```std::pair``` and ```std::make_pair```
```std::pair``` is a container which can have two elements of **different types**. ```std::make_pair``` can make a pair of **different types**.
```c++
#include <iostream>
#include <utility>

int main() {
    std::pair<char, int> ourPair;
//        first ↑     ↑ second

    studentInfo.first = 'a';  //fist element (char)
    studentInfo.second = 15;  //second element (int)

    std::cout << "First element is " << ourPair.first << "\n";
    std::cout << "Second element is " << ourPair.second << "\n";
}
```
```
First element is a
Second element is 15
```
