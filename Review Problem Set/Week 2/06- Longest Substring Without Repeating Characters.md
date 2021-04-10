https://leetcode.com/problems/longest-substring-without-repeating-characters/


```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        globalMax = 0
        localMax = 0
        uniqueList = []
        for char in s:
            if char not in uniqueList:
                localMax += 1
                uniqueList.append(char)
            else:
                uniqueList = uniqueList[uniqueList.index(char)+1:]
                uniqueList.append(char)
                localMax = len(uniqueList)
            globalMax = max(globalMax, localMax)
        return globalMax
```
