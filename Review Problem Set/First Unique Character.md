https://leetcode.com/problems/first-unique-character-in-a-string/submissions/

```python
class Solution(object):
  def firstUniqChar(self, s):
      """
      :type s: str
      :rtype: int
      """
      countDict = Counter(s)
      answerList = []
      for key, value in countDict.items():
          if value > 1:
              continue
          elif value == 1:
              answerList.append(s.index(key))

      if len(answerList) > 0:
          return min(answerList)
      else:
          return -1
```
