# Leetcode Problem:

Given an array A of integers, return true if and only if we can partition the array into three non-empty parts with equal sums.
Formally, we can partition the array if we can find indexes i+1 < j with (A[0] + A[1] + ... + A[i] == A[i+1] + A[i+2] + ... + A[j-1] == A[j] + A[j-1] + ... + A[A.length - 1])
 
Example 1:
Input: [0,2,1,-6,6,-7,9,1,2,0,1]
Output: true
Explanation: 0 + 2 + 1 = -6 + 6 - 7 + 9 + 1 = 2 + 0 + 1
Example 2:
Input: [0,2,1,-6,6,7,9,-1,2,0,1]
Output: false

My Solution scored faster than 99.92% of python solutions. 
The key to the speed is that I ignored checking for the "third" part. 
If the first 2 achieve the condition, then definitely the third does, no need to waste time to check it.


```
class Solution(object):
    def canThreePartsEqualSum(self, A):
        sum_1 = 0
        sum_2 = 0
        S = sum(A)/3
        for i in range(len(A)-1):
            sum_1 += A[i]
            if sum_1 == S:
                break
        else:
            return False
        
        
        for j in range(i+1,len(A)-1):
            sum_2 += A[j]
            if sum_2 == S:
                break
        else:
            return False
        
        return True
```
