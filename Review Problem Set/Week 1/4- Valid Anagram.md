
https://leetcode.com/problems/valid-anagram/submissions/


This solution seems slow, needs optimization/improvements.
```
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        countDict = {}
        sList = list(s)
        tList = list(t)
        if len(sList) != len(tList):
            return False
        
        for character in sList:
            countDict[character] = countDict.get(character,0) + 1
            
        for character in tList:
            if countDict.get(character,0) == 0:
                return False
            else:
                countDict[character] = countDict.get(character,0) - 1
                if countDict[character] == 0:
                    del countDict[character]
                    
        return not countDict
            
            
```
