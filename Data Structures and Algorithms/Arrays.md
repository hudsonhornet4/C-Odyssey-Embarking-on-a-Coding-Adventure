# Introduction to Arrays in C++
Now we'll dive into the fundamental data structure known as an array in C++. 
Arrays are collections of elements, each identified by an index or position. They are widely used for storing and organizing data in a contiguous memory block.
Arrays provide quick access to elements based on their index, making them efficient for various programming tasks. Let's dive into.
- - - -
### Declaration ✨
In C++, we can declare an array with square brackets ```[]``` and specifying the number of elements in the array. For example:
```c++
// Declaration of an array of size 5
int array[5] = {1, 2, 3, 4, 5};
```
As you can see, we've created an array with name ```array``` with '5' elements, and each element is assigned a value using the curly braces ```{}```.
### Accessing Our Array Elements 🎯
Array elements are accessed using their index, which starts from 0. For example, to access the third element in the ```array``` array, we use:
```c++
//                       ↓'2' because we start to count indexes from '0', so third element is 2.
int thirdElement = array[2];  //we point at '3' in our array
//                   ↑ name of our array
```
Remember, that the index "2" is the third element because array indices start from 0.
## Operations ⚙️
### Traversing an Array 🚶‍♂️
We can loop through all the elements in an array using a "for" loop. For example:
```c++
for (int i = 0; i < 5; i++) {
    cout << array[i] << " ";
}
```
That will print out all elements in our array.
```
1 2 3 4 5
```
### Modifying an Array ✏️
```c++
array[3] = 10;
```
Now our array looks like this:
```c++
int array[5] = {1, 2, 3, 4, 5}; //Before
int array[5] = {1, 2, 3, 10, 5}; //After
```
## LeetCode🔧🟨 Example:
![LeetCode - Array](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/a8c4adb5-a26e-4eac-9047-3e9c7876db47)
They give us the examples, where it says that if one element adding with another element in array will equal target, then we need to add these elements in our ```vector<int> result```.
```c++
#include <vector>

vector<int> twoSum(vector<int>& nums, int target) {
    vector<int> result; //We will output this, here we will have our elements, which together will be equal our target, 

    // Nested 'for' loop to check all possible pairs of numbers in the array.
    for (int i = 0; i < nums.size(); i++) { //it will start from first element in array, for examlpe if an array is [1,2,3,4,5], it wil start from 1
        for (int j = i + 1; j < nums.size(); j++) {  
//since our 'i' is 0, it will start from 1, for example if an array is [1,2,3,4,5], 'i' will start from 1, and 'j' from '2'
            if (nums[i] + nums[j] == target) {// If the sum of the two numbers equals the 'target' value, we found the pair.
                //if we found our elements which equal == targen, we add them in our vector(array) 'result'
                result.push_back(i); // Index of the first number in the pair.
                result.push_back(j); // Index of the second number in the pair.
                return result;       //Return
            }
        }
    }

    return result;     //if elements which equal target are not found , we return empty
}
```
![ArrayLeetCodeDrawing](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/912150ca-4c4f-464b-8aef-3ea8e8f6d3ce (I tried to draw well 🙂 ))

