# Question
Given a non-empty array of integers, every element appears twice except for one. Find that single one.

Note:

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

Example 1:

Input: [2,2,1]
Output: 1
Example 2:

Input: [4,1,2,1,2]
Output: 4

[Question Link](https://leetcode.com/problems/single-number/) 

# Solution
The brute force way to solve this problem is to count all the existing numbers, then we will have a set of numbers, all have a count of 2 except for one which has a count of 1. Then we will return that specific number, seems straight forward, right?

Well, that solution works, but it is not by far an optimum one. Why? First of all, depending on the implementation of the other bucket , whether it is a list or dictionary, then this could be with complexity O(n<sup>2</sup> ) or O(n) if it was implemented as hash map (dictionary in python). Second, why all that wasted memory? Who said that we need to store & count all that just to return the needed element? Let's see a more optimized solution.

First, create another bucket (list, dictionary,...?), then loop through our number array. If the number already exists in the other bucket, then remove it. That's the difference here, we already know that the all the numbers - except for one - exists twice, so the fact that it already exists in the other bucket, means that it is one of those existing twice in the array, so we don't need to keep it anymore, that's why we can remove it. After completing the loop, we will have only one element in the bucket, and that is the needed number.

Now, the complexity of that algorithm. We have one loop through our array, and we have another 'search' in the other bucket. Here is the trick, if that other bucket is implemented as a list, then here is another O(n) and thus the total complexity is O(n<sup>2</sup> ). But if that bucket is implemented as a hash map (dictionary in python), with a linear search complexity, then we are good and the overall complexity is O(n).


# Code
``` python
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        new_dict = {}
        for number in nums:
            if number in new_dict.keys():
                del new_dict[number]
            else:
                new_dict[number] = 1
        return new_dict.keys()[0]
```        
        
      
