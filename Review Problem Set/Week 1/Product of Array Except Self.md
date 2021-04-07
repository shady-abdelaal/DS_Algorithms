https://leetcode.com/problems/product-of-array-except-self/submissions/

Runtime: 208 ms, faster than 78.37% of Python online submissions for Product of Array Except Self

But the solution is not optimal, it needs refactoring and better design.

```
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        result = 0
        zeroFlag = False
        zeroCount = 0
        firstPass = True
        n = len(nums)
        for element in nums:
            if element == 0:
                zeroFlag = True
                zeroCount +=1
            else:
                if firstPass:
                    result = 1
                    firstPass = False
                result = result*element
        
        answer = []
        if zeroCount >= 2:
            answer = [0] * n
        else:
            
            for i in range(len(nums)):
                if zeroFlag:
                    if nums[i] == 0:
                        answer.append(result)
                    else:
                        answer.append(0)
                else:
                    answer.append(result/nums[i])

        return answer
        
            
        
```
