# Introduction to Stack 📚
A stack is a fundamental data structure that follows the Last-In, First-Out (aka LIFO) principle. 
It can be visualized as a collection of elements arranged like a stack of plates, where the last plate added is the first one to be removed.
Stacks are commonly used in programming to manage the order of function calls, track execution history, and solve various algorithmic problems.
## Stack Operations 📝
Stacks support two operations:
- **Push**, i.e. adding an element to the top of the stack.
- **Pop**, i.e. removing the top element from the stack.
In addition to these, stacks often provide an operation to examine the top element without removing it:
- 👁️ **Peek** **(or Top)**, i.e. retrieve the top element without modifying the stack.
## Stack Implementation 🥞😋
Stacks can be implemented using arrays or our favourite linked lists. 
Here, we'll focus on the array-based implementation. We'll define a ```Stack``` class with the following components:
- An integer to keep track of the current size of the stack.
- A dynamic array to store the elements of the stack.
- Functions, which do:  push, pop, and peek operations.
```c++
#include <iostream>
#define MAX_SIZE 100; // we defined maximum size of our stack

class Stack {
private:
    int data[MAX_SIZE]; // Array to store stack elements
    int size;           // Current size of the stack

public:
    Stack() : size(0) {}

    // Check if our stack is empty
    bool isEmpty() const {
        return size == 0;            //if our size is 0 (nothing), then we will return true, if more , then return false
    }

    // Check if our stack is full
    bool isFull() const {
        return size == MAX_SIZE;      //if our size is 100 (look up), then it will return true, if less, then false
    }

    // Push an element onto the stack
    void push(int element) {
        if (isFull()) {      //If isFull is true then .. 
            std::cout << "Cannot push element, because our stack is full.\n";
            return;
        }
        data[size++] = element; // Add the element to the top of the stack, also increasing the size
    }

    // Pop (aka remove) the top element from the stack
    void pop() {
        if (isEmpty()) {    //If isEmpty is true then ..
            std::cout << "Cannot pop element, because stack is empty.\n";
            return;
        }
        size--; // Decreasing the size to remove the top element from the stack
    }

    // Return the value of the top element without removing it
    int peek() const {
        if (isEmpty()) {
            std::cout << "Stack is empty.\n";
            return -1;  //ERROR 
        }
        return data[size - 1]; // Return the value of the top element in the stack
    }
};

int main(int argc, char* argv[]) {
    Stack stack;
  //adding in our stack
    stack.push(1); 
    stack.push(4);
    stack.push(8);

    std::cout << "Top element is " << stack.peek() << "\n"; // Output: Top element is 8

    stack.pop();  //deleting
    std::cout << "Top element after pop is " << stack.peek() << "\n"; // Output: Top element after pop is 4

    return 0;
}
```


## LeetCode example 🟨🛠️
Today, for our exampel I chose the task [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/ (Yes, that's indeed Valid Parentheses))
![LL3](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/9b17fffa-8a49-47a3-ba12-a709d487ebe4)
```c++
#include <iostream>
#include <stack>     //Pay attention on this as well, dont forget.
using namespace std; //dont pay attention on this 
bool isValid(string s) {

    stack<char> our_Stack; //created a stack

    for (char ch : s) {
        if (ch == '(' || ch == '[' || ch == '{') {
            // If the character is an opening bracket, push it onto the stack.
            our_Stack.push(ch);
        } else {
            // If the character is a closing bracket, check if the stack is empty.
            if (our_Stack.empty()) {
                return false; // Stack is empty
            }

            // Compare the closing bracket with the top element of the stack.
            char topBracket = our_Stack.top();
            if ((ch == ')' && topBracket == '(') ||
                (ch == ']' && topBracket == '[') ||
                (ch == '}' && topBracket == '{')) {
                // Matching closing bracket found, pop the corresponding opening bracket.
                our_Stack.pop();
            } else {
                // Mismatch in closing bracket or top element in the stack
                return false;
            }
        }
    }

    // If the stack is empty, all brackets were correctly matched.
    // Otherwise, there are some unclosed opening brackets.
    return our_Stack.empty();
}
```





