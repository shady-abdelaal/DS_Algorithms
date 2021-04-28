https://leetcode.com/problems/top-k-frequent-elements/

Straight forward answer with complexity `O(N log N)` 
There is another implementation with `heap` which achieves complexity of `O(N log K)`

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
