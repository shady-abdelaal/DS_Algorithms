# Leet Code Problem (Missing Number):

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

Example 1:

Input: [3,0,1]
Output: 2
Example 2:

Input: [9,6,4,2,3,5,7,0,1]
Output: 8


**My Solution:** 
With Runtime: 100 ms, ***faster than 99.85%*** of Python online submissions for Missing Number.

``` python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if len(nums) == 1:
            if nums[0] == 0:
                return 1
            else:
                return 0
        actual = sum(nums)
        supposed = sum(range(len(nums) + 1))
        missing = supposed - actual
        return missing
```
