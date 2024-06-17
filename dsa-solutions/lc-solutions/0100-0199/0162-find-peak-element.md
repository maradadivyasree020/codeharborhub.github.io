---
id: find-peak-element
title: Find Peak Element (LeetCode)
sidebar_label: 0162-Find Peak Element
tags:
  - Array
  - Binary Search
description: Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.
sidebar_position: 0162
---

## Problem Description

A peak element is an element that is strictly greater than its neighbors.

Given a 0-indexed integer array nums, find a peak element, and return its index. If the array contains multiple peaks, return the index to any of the peaks.

You may imagine that nums[-1] = nums[n] = -∞. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

You must write an algorithm that runs in O(log n) time.

### Example 1

- **Input:** `nums = [1,2,3,1]`
- **Output:** `2`
- **Explanation:** 3 is a peak element and your function should return the index number 2.

### Example 2

- **Input:** ` nums = [1,2,1,3,5,6,4]`
- **Output:** `5`
- **Explanation:** Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.

### Constraints

- `1 <= nums.length <= 1000`
- `-2^31 <= nums[i] <= 2^31 - 1`
- `nums[i] != nums[i + 1] for all valid i.`

## Approach
- 1. We initialize two pointers, left and right, which represent the boundaries of our current search interval. left is set to 0, and right is set to the length of the array minus one (len(nums) - 1).
 
- 2. We enter a while loop that continues as long as left is less than right, ensuring that we are still considering a range of possible positions for a peak element.
      
- 3. Inside the loop, we calculate the midpoint of the current search interval as mid = (left + right) >> 1. The >> 1 operation is a bitwise shift to the right by 1 bit, which is equivalent to dividing by two, but it's often faster.

- 4. We then compare the element at the mid position with the element immediately to its right (nums[mid + 1]).
     
- 5. If nums[mid] is greater than nums[mid + 1], the peak must be at mid or to the left of mid. Thus, we set right to mid, effectively narrowing the search interval to the left half.



### Solution Code

#### C++

```c++
class Solution {
public:
    string reverseWords(string s) {
        int i = 0, j = s.size() - 1;
        while (i <= j && s[i] == ' ') i++;   
        while (j >= i && s[j] == ' ') j--;   
        s = s.substr(i, j - i + 1);          
        vector<string> words;                
        stringstream ss(s);                  
        string word;
        while (ss >> word) {                 
            words.push_back(word);           
        }
        string out = "";
        for (int i = words.size() - 1; i > 0; i--) {
            out += words[i] + " ";
        }
        return out + words[0];               
    }
};

```

#### java
```java
public class Solution {
    public String reverseWords(String s) {
        int i = 0, j = s.length() - 1;
        while (i <= j && s.charAt(i) == ' ') i++;  
        while (j >= i && s.charAt(j) == ' ') j--; 
        s = s.substring(i, j + 1);                
        String[] words = s.split("\\s+");         
        StringBuilder out = new StringBuilder();
        for (int k = words.length - 1; k > 0; k--) {
            out.append(words[k]).append(" ");
        }
        return out.append(words[0]).toString();       
    }
}

```

#### Python
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        i, j = 0, len(s) - 1
        while i <= j and s[i] == ' ':
            i += 1  
        while j >= i and s[j] == ' ':
            j -= 1  
        s = s[i : j + 1] 
        words = s.split()  
        out = []
        for k in range(len(words) - 1, 0, -1):
            out.append(words[k])
        out.append(words[0])
        return ' '.join(out) 
```

#### Conclusion
The above solutions use two-pointers approach to reverse the string.
  - 1. Time complexity: O(n)
  - 2. Space complexity: O(m)( where M is the total number of words in the input string. )
