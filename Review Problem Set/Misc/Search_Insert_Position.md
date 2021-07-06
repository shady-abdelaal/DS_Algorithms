https://leetcode.com/problems/search-insert-position/


```python
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left = 0
        right = len(nums) - 1
        
        while left <= right:
            mid = (right + left ) // 2
            
            if target > nums[mid]:
                left = mid +1
                
            elif target < nums[mid]:
                right = mid -1
            
            else:
                return mid
            
        return right +1
```
