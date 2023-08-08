# Linked List 📎
A Linked List is a linear data structure composed of nodes, where each node contains data and a reference (or pointer) to the next node in the sequence. 
It doesnt require a contiguous block of memory like arrays, making it more flexible in size and insertion operations.
- - - -
###  Creating and Accessing Nodes 🔗
To create a Linked List, we define a Node structure containing the data and the pointer to the next node. 
For example , a simple Node structure in C++:
```c++
struct Node {
    int data;    //data in a node
    Node* next;  //pointer at next node
};
```
Each Node holds data of type "int" and a pointer to the next Node in the list. 
The ```next``` pointer is initialized as ```nullptr``` to indicate the end of the list.



### Linked List Head 🌐
The starting point of the Linked List is known as the "head." It serves as the reference to the first node in the list. 
If the Linked List is empty, the head is set to ```nullptr```.
For example: 
```c++
// Creating a Linked List with two nodes
Node* head = new Node();
head->data = 5;
head->next = new Node(); //creating a node, let's call it 'Bob'
head->next->data = 10;   // Bob has value '10'
head->next->next = nullptr; //nothing is after our "Bob"
```
![LL1](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/3e474adf-4c55-4cc9-b6f0-dbe1ffd993f5)

## Insertion Operations 🔄
There are different ways to insert elements into a Linked List:
### Insert at the Beginning 🏁
Adding a new node at the beginning involves updating the ```next``` pointer of the new node to point to the current head and then updating the head to the new node.
For example:
```c++
void insertAtBeginning(Node*& head, int newData) {    //newData can be anything, '10', '5' , whatever, any 'int'
    Node* newNode = new Node();    //creating a new Node
    newNode->data = newData;       //giving it our newData
    newNode->next = head;          //connecting it in the beginning to head
    head = newNode;                
}
```
### Insert at the End 🏁
To add a node at the end, we traverse the list until we reach the last node (where ```next``` is ```nullptr```), and then create a new node and update the ```next``` pointer of the last node to point to the new node.
For example:
```c++
void insertAtTheEnd(Node*& head, int newData) {
    Node* newNode = new Node();    //creating a new Node
    newNode->data = newData;       //adding it our newData
    newNode->next = nullptr;      //after our newNode we have nothing, so that means that's the end

    if (head == nullptr) {
    // If the linked list is empty (head is nullptr),
    // set the new node as the head of the linked list.
    head = newNode;
} else {
    // If the linked list is not empty (head is not nullptr),
    // we need to find the last node in the linked list to
    // attach the new node at the end.

    // Create a pointer 'current' and set it to the head node.
    Node* current = head;

    // Traverse the linked list until we reach the last node
    // (i.e., the node whose 'next' pointer is nullptr).
    while (current->next != nullptr) {
        current = current->next;
    }

    // After the loop, 'current' points to the last node.
    // Set the 'next' pointer of the last node to the new node,
    // effectively attaching the new node at the end of the list.
    current->next = newNode;
}
}
```
### Insert at Specific Position 🤔🎯
To insert at a specific position, we find the node before the desired position, update its ```next``` pointer to the new node, and set the ```next``` pointer of the new node to the node that was previously at that position.
For example:
```c++
void insertAtPosition(Node*& head, int newData, int position) {
    // Create a new node and set its data to the given 'newData'.
    Node* newNode = new Node();
    newNode->data = newData;
    newNode->next = nullptr;

    // If 'position' is 0, insert the new node at the beginning.
    if (position == 0) {
        // Update the 'next' pointer of the new node to point to the current head.
        newNode->next = head;
        // Update the 'head' to point to the new node, making it the new head.
        head = newNode;
    } else {
        // If 'position' is not 0, we need to find the node before the desired position.

        // Create a pointer 'current' and set it to the head node.
        Node* current = head;
        // Initialize a variable 'currentPosition' to keep track of the current position.
        int currentPosition = 0;

        // Traverse the linked list until we reach the node before the desired position
        // or until the end of the linked list (current is nullptr).
        while (current != nullptr && currentPosition < position - 1) {
            current = current->next;
            currentPosition++;
        }

        // If 'current' is nullptr, it means 'position' is out of range (too large).
        // Print an error message and return from the function.
        if (current == nullptr) {
            cout << "Position out of range." << endl;
            return;
        }

        // Attach the new node at the desired position in the linked list.
        // Update the 'next' pointer of the new node to point to the node after 'current'.
        newNode->next = current->next;
        // Update the 'next' pointer of 'current' to point to the new node,
        // effectively inserting the new node into the linked list.
        current->next = newNode;
    }
}
```
### Searching in Linked List 🔎
To find an element in the Linked List, we traverse the list from the head, comparing the data of each node with the target value. 
If the target is found, we return the node. If not, we continue until the end of the list.
For example:
```c++
Node* searchTarget(Node* head, int target) {
    Node* current = head;              //setting current 
    while (current != nullptr) {       //while current will not reach the end ('nullpr'
        if (current->data == target) { //if current node's data is equal target .. 
            return current;            //.. then we return current node
        }
        current = current->next;       //while we havent reach the end and while havent find correct node which equal target - we continue to move forward
    } 
    return nullptr; // Returning nothing if we didnt find any and reached the end
}
```
## Deletion Operations 🗑️
Deleting a node from the Linked List involves updating the ```next``` pointer of the previous node to skip the node to be deleted and freeing its memory.
For examplle:
```c++
void deleteNode(Node*& head, int target) {
    if (head == nullptr) {
        return; // If our list is empty, we have nothing to delete
    }

     // Check if the target is present in the first node (head) of the linked list.
    if (head->data == target) {
        // If the target is found in the head node, we need to remove the head.

        // Create a temporary pointer 'temp' and set it to the current head.
        Node* temp = head;
        // Update our 'head' to point to the next node after the current head
        // effectively removing the current head from the linked list.
        head = head->next;
        // Delete the node pointed to by 'temp' (previous head) to free its memory.
        delete temp;
        // Return from the function since the target is found and deleted.
        return;
    }

    // If the target is not in the head node, we need to find the node before the target.

    // Create a pointer 'current' and set it to the head node.
    Node* current = head;

    // Traverse the linked list until we reach the last node (current->next is nullptr)
    // or until we find the node whose 'next' node contains the target.
    while (current->next != nullptr) {
        if (current->next->data == target) {
            // If the target is found in the 'next' node of 'current'...
            // ...then we need to remove that node from the linked list.

            // Create a temporary pointer 'temp' and set it to the node to be deleted.
            Node* temp = current->next;
            // Update our 'next' pointer of 'current' to skip the node to be deleted ...
            // effectively removing the node from the linked list.
            current->next = current->next->next;
            // Delete the node pointed to by 'temp' to free its memory.
            delete temp;
            // Return from the function since the target is found and deleted.
            return;
        }
        // Move to the next node in our list.
        current = current->next;
    }
}
```
### Traversing a Linked List 🚶‍♂️
To traverse the Linked List, we start at the head and move from node to node using the ```next``` pointers until we reach the end (when the ```next``` pointer is ```nullptr```). 
During traversal, we can access and process each node's data as needed.
For example:
```c++
void traverse(Node* head) {
    Node* current = head;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << "\n";
}
```

## LeetCode Example 🟨🛠️
As an example for our topic , I will choose [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/ (Official LeetCode Website with the task))
![LL2](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/dd40c954-1b96-4c37-958c-3101d7e8ef4c)

```c++
struct ListNode {
    int val;        //instead of our familiar 'data' we have 'val', but nothing changes
    ListNode* next;
};

ListNode* deleteDuplicates(ListNode* head) {
    if (head == nullptr) {
        return nullptr; // If our list is empty, then we return 'nullptr' (nothing)
    }

     // Create a pointer 'current' and set it to our head node.
    ListNode* current = head;

    // Traverse the linked list until we reach our last node
    // (current->next is nullptr, meaning no more nodes after this).
    while (current->next != nullptr) {
        // Check if the current node's value is the same as the next node's value.
        if (current->val == current->next->val) {
            // If the current node's value is the same as the next node's value,
            // it means there is a duplicate.

            // Create a temporary pointer 'temp' and set it to the next node.
            ListNode* temp = current->next;
            // Update the 'next' pointer of 'current' to skip the next node,
            // effectively removing the duplicate node from the linked list.
            current->next = current->next->next;
            // Delete the node pointed to by 'temp' to free its memory (remove duplicate), mwhaha.
            delete temp;
        } else {
            // If the current node's value is not the same as the next node's value,
            // move to the next node in the linked list.
            current = current->next;
        }
    }

    // After traversing the linked list and removing duplicates,
    // return the head of the modified linked list.
    return head;
}
}

```










