https://leetcode.com/problems/group-anagrams/

Very elegant solution and very intuitive.
```python
class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[List[int]]
        :rtype: List[List[int]]
        """
        
        intervals.sort(key=lambda x: x[0])
        mergedIntervals = []
        for interval in intervals:
            if not mergedIntervals or mergedIntervals[-1][1] < interval[0]:
                mergedIntervals.append(interval)
            else:
                mergedIntervals[-1][1] = max(interval[1], mergedIntervals[-1][1])
            
        return mergedIntervals
```

Some more optimization utilizing python brilliant dictionary operations, it lead to a much shorter run time


```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """    
        sortedStringsDict = {}
        for element in strs:
            sortedString = ''.join(sorted(element))
            sortedStringsDict[sortedString] = sortedStringsDict.get(sortedString, []) + [element]
            
        return sortedStringsDict.values()
```
