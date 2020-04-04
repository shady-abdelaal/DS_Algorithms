``` python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        elements_num = len(nums)
        i = 0
        for counter in range(0, elements_num - 1):
            if nums[i] == 0:
                nums.append(0)
                del nums[i]
            else:
                i = i+1
```
        
