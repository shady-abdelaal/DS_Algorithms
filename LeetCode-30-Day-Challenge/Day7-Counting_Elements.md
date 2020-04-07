# Counting Elements

Given an integer array arr, count element x such that x + 1 is also in arr.

If there're duplicates in arr, count them seperately.

 

Example 1:

```Input: arr = [1,2,3]
Output: 2
Explanation: 1 and 2 are counted cause 2 and 3 are in arr.
```

Example 2:

```Input: arr = [1,1,3,3,5,5,7,7]
Output: 0
Explanation: No numbers are counted, cause there's no 2, 4, 6, or 8 in arr.
```

Example 3:

```Input: arr = [1,3,2,3,5,0]
Output: 3
Explanation: 0, 1 and 2 are counted cause 1, 2 and 3 are in arr.
```
Example 4:

```Input: arr = [1,1,2,2]
Output: 2
Explanation: Two 1s are counted cause 2 is in arr.
```

# Solution
Elements counting is a very important pattern that often appears in different forms. In situations like this one where we find ourselves 
in need of a 'count' as an attribute to each element and at the same time we need extensive search within this object. Then the dictionary is the solution.
The idea is to count all the numbers in the array, and then loop through them, and see if another element exists that is more than the one at hand by 1 or not.
If yes, increment the count of the current element to the global count. If not, then this can be discarded, this element is not to be counted.
For more illustration about the element counting in python. Refer to [this tutorial](https://github.com/shady-abdelaal/DS_Algorithms/blob/master/Counting_Problems.md). 

# Code
```python
class Solution(object):
    def countElements(self, arr):
        """
        :type arr: List[int]
        :rtype: int
        """
        counts = 0
        counting_dictionary = {}
        for element in arr:
            counting_dictionary[element] = counting_dictionary.get(element, 0) + 1
        
        for one_number in counting_dictionary.keys():
            if (one_number + 1) in counting_dictionary.keys():
                counts = counts + counting_dictionary[one_number]
        return counts
 
```
