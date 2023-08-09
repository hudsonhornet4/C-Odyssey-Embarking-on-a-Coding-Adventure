# Introduction to Hashing 📥
Hashing is like creating a super-efficient index system for a massive library. 
Imagine you are managing a vast collection of books, and instead of looking through every bookshelf, you have magical keys that point directly to where each book is stored. 
Let's dive into this concept using real-world examples, emojis, and plain language.
## Understanding Hashing 🏗️
Hashing is a clever way to speed up finding stuff. 
You take something, like a word or a number, and transform it into a special code using a formula.
This code helps you find things quickly, just like how barcodes help cashiers scan items fast at the store.
## Real-World Scenario - Online User Accounts 📬
Think about a website with many users. Each user has own unique username. 
Instead of searching through all usernames to find one, the website uses a hash code based on the username. 
This hash code guides the system to the right account in an instant.
## How Hashing Works 🔑
- Create the Code, i.e. apply a formula (hash function) to your data to generate a unique code (hash).
- Quick Navigation, i.e. this code points you to the exact spot where your data is stored, just like a treasure map leads you to the treasure.
- Fast Retrieval, i.e. instead of searching through everything, you can directly access what you need using the code.
## For example - Hashing Our Usernames 👨‍💻
```c++
#include <iostream>
#include <unordered_map>    //! DONT FORGET ABOUT THAT
int main() {
    std::unordered_map<std::string, std::string> user_accounts;

    // Adding usernames and corresponding passwords
    user_accounts["mia"] = "qwerty321";                 // 'mia' is nickname , 'qwerty321' is password
    user_accounts["bob"] = "bestPasswordInTheWorld";      // 'bob' is nickname, 'bestPasswordInTheWorld' is password

    std::string mia_Username = "mia";                      //here we find a password of our 'mia' (pass: qwerty321 🤫)
    std::cout << "Password for 'mia' is [" << userAccounts[mia_Username] << "]\n";    //Output: Password for 'mia' is [qwerty321]

}
```

## LeetCode Example 🟨🛠️:
The task I chose is [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/ (Longest Substring Without Repeating Characters))
![hashmaps1](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/900205f7-df8b-43e1-9030-53e2b6c3e505)
```c++
using namespace std;
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n = s.length(); // get the length of the input string 's'
        int maxLength = 0; // initialize the maximum length of the substring
        unordered_set<char> hashmap; // create a set to store unique characters
        int left = 0; // initialize the left pointer for the sliding window

        // traverse the string using the sliding window technique
        for (int right = 0; right < n; right++) {
            if (hashmap.count(s[right]) == 0) {    //here we check if added letter is not already in set, if it is, then it supposed to be >0
              hashmap.insert(s[right]);            //if the letter we want to add is not equal 0 (means we dont have it in our set ) then we add
              maxLength = max(maxLength, right - left + 1); //updating maximum length
            } else {
              // If the character is already in the set, remove characters from the left
                while (hashmap.count(s[right])) {
                      hashmap.erase(s[left]); // Remove character from the left
                      left++; // Move the left pointer
        }
                hashmap.insert(s[right]); // Add the current character to the set
    }
}

          return maxLength; // Return the length of the longest substring
};
```
## Better explanation 🤌
For example our input is **"abcabcbb"**

**Initialization**:

- maxLength = 0
- hashmap = {}
- left = 0
- right = 0





### 1️⃣ 1th Iteration (right at index 0, character 'a'):

- ```hashmap``` is empty, so we add 'a' to it.
- maxLength is updated to 1 (right - left + 1).
- left and right remain at 0.
<br>🗃️ How our hashmap looks like: **{'a'}** 🗃️</br>




### 2️⃣ 2nd Iteration  (right at index 1, character 'b'):

- 'b' is not in hashmap, so we add it and update maxLength to 2.
- left and right remain at 0 and 1, respectively.
<br>🗃️ How our hashmap looks like: **{'a', 'b'}** 🗃️ </br>



### 3️⃣ 3rd Iteration (right at index 2, character 'c'):

- 'c' is not in hashmap, so we add it and update maxLength to 3.
- left and right remain at 0 and 2, respectively.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>






### 4️⃣ 4th Iteration (right at index 3, character 'a'):

- 'a' is already in hashmap.
- The loop is entered to remove characters from the left.
- 'a' is removed from hashmap and left is incremented to 1.
- The loop exits as 'a' is no longer in hashmap.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>






### 5️⃣ 5th Iteration (right at index 3, character 'a' again):

- 'a' is not in hashmap, so we add it and update maxLength to 3.
- left and right remain at 1 and 3, respectively.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>





### 6️⃣ 6th Iteration (right at index 4, character 'b' again):

- 'b' is already in hashmap.
- The loop is entered to remove characters from the left.
- 'b' is removed from hashmap and left is incremented to 2.
- The loop exits as 'b' is no longer in hashmap.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>





### 7️⃣ 7th Iteration (right at index 5, character 'c' again):

- 'c' is already in hashmap.
- The loop is entered to remove characters from the left.
- 'c' is removed from hashmap and left is incremented to 3.
- The loop exits as 'c' is no longer in hashmap.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>





### 8️⃣ 8th Iteration (right at index 6, character 'b' again):

- 'b' is already in hashmap.
- The loop is entered to remove characters from the left.
- 'b' is removed from hashmap and left is incremented to 4.
- The loop exits as 'b' is no longer in hashmap.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>




### 9️⃣ 9th Iteration (right at index 7, character 'b' again):

- 'b' is not in hashmap, so we add it and update maxLength to 3.
- left and right remain at 5 and 7, respectively.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>





### 🔟 10th Iteration (right at index 8, character 'b' again):

- 'b' is not in hashmap, so we add it and update maxLength to 3.
- left and right remain at 5 and 8, respectively.
<br>🗃️ How our hashmap looks like: **{'a', 'b', 'c'}** 🗃️</br>



## 🥳 Our final result:

### maxLength is 3, which is the length of the longest substring without repeating characters.


