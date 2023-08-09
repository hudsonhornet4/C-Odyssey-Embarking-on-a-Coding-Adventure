# Binary Search 🔍🧐
Binary Search is a powerful algorithm used to find a specific element in a sorted array. 
It follows the "divide and conquer" strategy, repeatedly dividing the search space in half to narrow down the search.
## How Binary Search Works:
- 1️⃣ **Initialization**, you need to define two pointers, left and right, which initially encompass the entire array.
- 2️⃣ **Middle Element**, then calculate the middle index, mid, as the average of left and right.
- 3️⃣ **Comparison**, compare the element at index mid with the target element.
  - If they match, the search is successful and mid is returned as the index.
  - If the element at mid is less than the target, narrow the search to the right half (set left = mid + 1).
  - If the element at mid is greater than the target, narrow the search to the left half (set right = mid - 1).
- 4️⃣ **Repeat**, continue dividing the search space and comparing until left exceeds right (search space is empty).
For example we need to find '13' in this **sorted** array:
### 5, 2, 1, 55, 32, 11, 13, 35, 22, 18
## Step 1: Initialization
- ```left``` = 0, ```righ```t = 9
- ```mid``` = (0 + 9) / 2 = 4, element at ```mid``` is 32



## Step 2: Comparison
- 32 < 11 (target), so narrow the search to the right half
- ```left``` = 5, ```right``` = 9



## Step 3: Repeat

- ```mid``` = (5 + 9) / 2 = 7, element at ```mid``` is 35
- 35 > 11 (target), so narrow the search to the left half
- ```left``` = 5, ```right``` = 6


## Step 4: Repeat

- ```mid``` = (5 + 6) / 2 = 5, element at ```mid``` is 11
- 11 == 11 (target found), return mid as index



## LeetCode Example 🟨🛠️
For our example I chose [4. Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)
![BS1](https://github.com/hudsonhornet4/C-Odyssey-Embarking-on-a-Coding-Adventure/assets/118293314/d9e07481-38aa-447b-ab7c-a4beebf8e715)
```c++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        // Ensure nums1 is smaller or equal to nums2 in size
        if (nums1.size() > nums2.size()) {
            return findMedianSortedArrays(nums2, nums1);
        }
        
        int m = nums1.size();
        int n = nums2.size();
        int left = 0, right = m; // binary search boundaries for partition
        
        while (left <= right) {
            int partition1 = (left + right) / 2; // Partition index for nums1
            int partition2 = (m + n + 1) / 2 - partition1; // corresponding partition index for 'nums2'
            
            int maxLeft1 = (partition1 == 0) ? INT_MIN : nums1[partition1 - 1]; // maximum element on the left side of 'nums1' partition
            int minRight1 = (partition1 == m) ? INT_MAX : nums1[partition1];     // minimum element on the right side of 'nums1' partition
            
            int maxLeft2 = (partition2 == 0) ? INT_MIN : nums2[partition2 - 1]; // maximum element on the left side of 'nums2' partition
            int minRight2 = (partition2 == n) ? INT_MAX : nums2[partition2];     // minimum element on the right side of 'nums2' partition
            
            if (maxLeft1 <= minRight2 && maxLeft2 <= minRight1) {
//                If the sum of the lengths of the two arrays is even, then the median is the average of the maximum value of the left half of the first array and the minimum value of the right half of the second array
//                Otherwise, the median is simply the maximum value of the left half of the first array.

                if ((m + n) % 2 == 0) {
                    return (max(maxLeft1, maxLeft2) + min(minRight1, minRight2)) / 2.0;
                } else {
                    return max(maxLeft1, maxLeft2);
                }
            } else if (maxLeft1 > minRight2) {
                // Move the partition towards the left in nums1
                right = partition1 - 1;
            } else {
                // Move the partition towards the right in nums1
                left = partition1 + 1;
            }
        }
        
        return 0.0; //  If the loop terminates, then the two arrays are empty, and therefore there is no median.
    }
};
```

- ```INT_MAX``` - The **maximum** value that can be stored in an integer variable of type ```int```.
- ```INT_MIN``` - The **minimum** value that can be stored in an integer variable of type ```int```.
For example, on a 32-bit system, ```INT_MIN``` is typically defined as ```-2147483648``` and ```INT_MAX``` is typically defined as ```2147483647```.
This means that an integer variable of type int on a 32-bit system can store any value from ```-2147483648``` to ```2147483647```, inclusive.
