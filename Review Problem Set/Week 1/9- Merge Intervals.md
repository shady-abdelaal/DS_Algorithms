Problem: https://leetcode.com/problems/merge-intervals/submissions/


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
