# LeetCode Problem:
https://leetcode.com/problems/degree-of-an-array/

Given a non-empty array of non-negative integers nums, the degree of this array is defined as the maximum frequency of any one of its elements.

Your task is to find the smallest possible length of a (contiguous) subarray of nums, that has the same degree as nums.

Example 1:
Input: [1, 2, 2, 3, 1]
Output: 2
Explanation: 
The input array has a degree of 2 because both elements 1 and 2 appear twice.
Of the subarrays that have the same degree:
[1, 2, 2, 3, 1], [1, 2, 2, 3], [2, 2, 3, 1], [1, 2, 2], [2, 2, 3], [2, 2]
The shortest length is 2. So return 2.
Example 2:
Input: [1,2,2,3,1,4,2]
Output: 6

**My Solution:**
``` python
class Solution(object):
    def findShortestSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        from collections import Counter
        test = Counter(nums).most_common()
        max_repetition = 0
        candidates_numbers = []
        
        for key, value in test:
            if value >= max_repetition:
                candidates_numbers.append(key)
                max_repetition = value
            else:
                break
        
        shortest_length = float('Inf')
        for candidate in candidates_numbers:
            index_1 = nums.index(candidate)
            index_2 = len(nums) -1  - list(reversed(nums)).index(candidate)
            if (index_2 - index_1 + 1) < shortest_length:
                shortest_length = index_2 - index_1 + 1
            
        return shortest_length
        
```

