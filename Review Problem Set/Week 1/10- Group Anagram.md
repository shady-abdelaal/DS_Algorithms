https://leetcode.com/problems/group-anagrams/

Very elegant solution and very intuitive.


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
