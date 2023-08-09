# Introduction to Trees 🌳
A tree is a hierarchical data structure that resembles an upside-down tree. 
It consists of nodes connected by edges, forming a structure with a root node at the top and various levels branching downwards.
Trees are widely used in computer science for organizing data in a way that allows efficient insertion, deletion, and retrieval.




## Tree Terminology 🌱
- **Node**: Each element in the tree, containing data and pointers to its child nodes.
- **Root**: The top node of the tree, from which all other nodes descend.
- **Parent**: A node that has child nodes.
- **Child**: Nodes directly connected to a parent node.
- **Leaf**: Nodes with no children, located at the bottom of the tree.
- **Depth**: The level of a node in the tree, with the root at level 0.
- **Height**: The length of the longest path from a node to a leaf.



## Binary Tree 🌲
A binary tree is a type of tree in which each node has at most two children, often referred to as the left child and the right child. 
Binary trees are common in many applications, including expression parsing, game trees, and hierarchical data storage.


## Binary Search Tree (aka BST) 🌳
A binary search tree is a binary tree where each node's left subtree contains nodes with values less than the node's value, and the right subtree contains nodes with values greater than the node's value. 
This property allows for efficient searching, insertion, and deletion operations.
<br> 🌲 For example:</br>
![BT1](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/ec4535e0-5d9e-4796-abaa-6b6009f0b336)


## Breadth-First Search (BFS) 🌐

BFS explores the tree level by level, starting from the root and moving to its children before visiting their children. 
It uses a queue to keep track of nodes at each level.

###  BFS Algorithm 📝
1. Enqueue the root node in the queue.
2. While the queue is not empty:
3. Dequeue a node.
4. Process the node's data.
5. Enqueue the node's children (if any) into the queue.
![BT2](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/bf492c97-75a6-4f51-9289-a9fd7673b891)
### 🌐 BFS traversal: 2 1 9 4 6 7




# Depth-First Search (DFS) 🌲

DFS explores the tree as deeply as possible along a branch before backtracking. It comes in three flavors: Preorder, Inorder, and Postorder.

## Preorder DFS Algorithm 📝

- Process the root node's data.
- Recursively traverse the left subtree.
- Recursively traverse the right subtree.
## Inorder DFS Algorithm 📝

- Recursively traverse the left subtree.
- Process the root node's data.
- Recursively traverse the right subtree.
## Postorder DFS Algorithm 📝

- Recursively traverse the left subtree.
- Recursively traverse the right subtree.
- Process the root node's data.
### 🌐 Example:
![BT3](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/85c5833a-1c30-4378-986d-192cf83a830e)

### <br> So now: </br>
- Preorder traversal is 1 6 3 2 8 4
- Inorder traversal is 3 6 2 1 8 4
- Postorder traversal is 3 2 6 4 8 1

## DFS LeetCode Example 🟨🛠️
For DFS I chose [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/ (Maximum Depth of Binary Tree))
![BT4](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/61173f2e-7a45-4701-afab-37821e5f4b5b)
```c++
#include <iostream> // Including the input/output stream library

using namespace std; // Using the standard namespace for simplicity

struct TreeNode {
    int val; // Value of the node
    TreeNode* left; // pointer to the left child node
    TreeNode* right; // pointer to the right child node
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {} // constructor to initialize our TreeNode
};

int maxDepth(TreeNode* root) { // Function to calculate the maximum depth of a binary tree
    if (!root) {
        return 0; // If our tree is empty, then it has depth 0
    }
    int leftDepth = maxDepth(root->left); // recursively calculate depth of left subtree
    int rightDepth = maxDepth(root->right); // recursively calculate depth of right subtree
    return max(leftDepth, rightDepth) + 1; // return the maximum depth + 1 for the current node
}
```
```c++
int main(int argc, char *argv[]) {
    // creating our first simple binary tree
    TreeNode* root = new TreeNode(3); // create root node with value 3
    root->left = new TreeNode(5); // attach left child with value 5
    root->right = new TreeNode(15); // attach right child with value 15
    root->right->left = new TreeNode(4); // attach left child of right child with value 4
    root->right->right = new TreeNode(9); // attach right child of right child with value 9
}
```
### <br>So this all will look like this:</br>
<br></br>
![BT5](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/a17368bd-0d01-4c2a-aee4-c60c2613a29d)

