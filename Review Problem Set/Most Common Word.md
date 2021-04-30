https://leetcode.com/problems/most-common-word/

```python
class Solution(object):
    def mostCommonWord(self, paragraph, banned):
        """
        :type paragraph: str
        :type banned: List[str]
        :rtype: str
        """
        
        normalized_str = ''.join([c.lower() if c.isalnum() else ' ' for c in paragraph])
        
        wordsList = normalized_str.split()
        countDict = dict()
        for word in wordsList:
            if word not in  set(banned):
                countDict[word] = countDict.get(word,0) + 1
        
        sortedDict = sorted(countDict.items(),key= lambda x:x[1], reverse=True)
        #print(sortedDict)
        return sortedDict[0][0]
```
