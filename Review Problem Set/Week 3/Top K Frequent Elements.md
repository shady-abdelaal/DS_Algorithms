https://leetcode.com/problems/top-k-frequent-elements/

Straight forward answer with complexity `O(N log N)` 
There is another implementation with `heap` which achieves complexity of `O(N log K)`

## Solution 1
Using python counter module. Achieved runtime faster than 30% of submissions.
```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        from collections import Counter
        
        countDict = Counter(nums)
        mostCommon = countDict.most_common(k) # Always remember that the Count returns [(element, frequency), (element2, frequency), ...]
        answerList = []
        for element in mostCommon:
            answerList.append(element[0])
        return answerList
```

## Solution 2
Using dictionary approach.
Runtime: 80 ms, faster than 88.51% of Python online submissions for Top K Frequent Elements.
Memory Usage: 16.9 MB, less than 32.17% of Python online submissions for Top K Frequent Elements.

```python
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        countDict = {}
        for element in nums:
            countDict[element] = countDict.get(element, 0) + 1
        
        sortedCountDict = sorted(countDict.items(), key=lambda x: x[1], reverse=True)
        answerList = []
        for i in range(k):
            answerList.append(sortedCountDict[i][0])
        return answerList
```
