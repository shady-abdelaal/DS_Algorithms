https://leetcode.com/problems/maximum-product-subarray/submissions/

DP Solution:
```python
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        dpMax = [None] * len(nums)
        dpMin = [None] * len(nums)
        
        ans = dpMax[0] = dpMin[0] = nums[0]
        for i in range(1, len(nums)):
            n = nums[i]
            if nums[i] > 0:
                dpMax[i] = max(n, dpMax[i-1] * n)
                dpMin[i] = min(n, dpMin[i-1] * n)
            else:
                dpMax[i] = max(n, dpMin[i-1] * n)
                dpMin[i] = min(n, dpMax[i-1] * n)
                
            
            
            ans = max(ans, dpMax[i])
        return ans
```
