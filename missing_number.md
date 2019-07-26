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
        return sum(range(len(nums) + 1)) - sum(nums)
```

How about some optimization? It is worth noting that `range()` function creates a list of the integers. So, instead of just wasting memory and execution time for the `sum()`. We can just use the "sum of arithmatic" series equation to find the sum.

```python
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
            
        n = len(nums) 
        total_sum = (n+1)*(len(nums)) / 2
        return total_sum - sum(nums)
```
