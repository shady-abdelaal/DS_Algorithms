https://leetcode.com/problems/top-k-frequent-words/


```python
class Solution(object):
    def topKFrequent(self, words, k):
        """
        :type words: List[str]
        :type k: int
        :rtype: List[str]
        """
        countDict = Counter(words)
        #print(countDict)
        sortedDict = sorted(countDict.items(), key= lambda x:(-x[1], x[0]))
        
        answer = []
        for element in sortedDict[:k]:
            answer.append(element[0])
 
        return answer
``` 
