# Introduction to Queues 🧑‍🤝‍🧑
A queue is another fundamental data structure commonly used in computer science. It follows the First-In, First-Out (aka FIFO) principle, 
similar to people waiting in line (queue) at a grocery store. 
In programming, queues are essential for managing tasks that need to be processed in the order they were added.
## Queue Operations 📝
As with stack, queues have two operations:
- **Enqueue**, i.e. adding an element to the back (end) of the queue.
- **Dequeue**, i.. removing the front (first) element from the queue.
<br>🤔Let's create an example of Enqueue and Dequeue: </br>
```c++
#include <iostream>
#include <queue>    //! DONT FORGET ABOUT THIS

int main() {
    queue<int> myQueue; //Creating our Queue

    // Enqueue elements into the queue
    myQueue.push(5);
    myQueue.push(12);
    myQueue.push(8);

    // Dequeue elements from the queue
    std::cout << "Dequeued element is " << myQueue.front() << endl; // Output: Dequeued element is 5
    myQueue.pop();

    std::cout << "Dequeued element is " << myQueue.front() << endl; // Output: Dequeued element is 12
    myQueue.pop();

    std::cout << "Dequeued element is " << myQueue.front() << endl; // Output: Dequeued element is 8
    myQueue.pop();

    return 0;
}
```
![LL5](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/e5398830-2329-4596-86e9-d1354461b447)

Additionally, we can examine the front element without removing it:
- **Front**, i.e. retrieve the front element without modifying the queue.
## Queue Implementation 🥪

Similar to stacks, queues can be implemented using arrays or linked lists. 
Here, we'll focus on the array-based implementation. 
Let's define a Queue class with the following components:

- 🧺 A dynamic array to store the elements of the queue.
- 🏁 Two pointers: one for the front and one for the back of the queue.
- 🔃 Functions to perform enqueue, dequeue, and front operations.

## LeetCode Example 🟨🛠️
As an example for Queues, I chose - [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/ (Binary Tree Level Order Traversal
))
![LL4](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/12059c5a-5381-4688-a1e0-3f25612a0de5)
```c++
#include <iostream>
#include <queue>
using namespace std;

struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> result; // to store the final result
    if (!root) {
        return result; // return empty result if the tree is empty
    }

    queue<TreeNode*> nodeQueue; // create a queue of tree nodes
    nodeQueue.push(root); // enqueue the root node

    while (!nodeQueue.empty()) {
        int levelSize = nodeQueue.size(); // get the number of nodes in the current level
        vector<int> levelValues; // to store values of nodes in the current level

        for (int i = 0; i < levelSize; i++) {
            TreeNode* currentNode = nodeQueue.front(); // get the front node in the queue
            nodeQueue.pop(); // dequeue our front node

            levelValues.push_back(currentNode->val); // store the value of the current node

            if (currentNode->left) {
                nodeQueue.push(currentNode->left); // enqueue left child if it exists
            }
            if (currentNode->right) {
                nodeQueue.push(currentNode->right); // enqueue right child if it exists
            }
        }

        result.push_back(levelValues); // store the values of the current level in the result
    }

    return result; // return our final result
}
```





