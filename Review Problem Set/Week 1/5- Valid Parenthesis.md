https://leetcode.com/problems/valid-parentheses/submissions/

This scored well. Runtime: 16 ms, faster than 85.90% of Python online submissions for Valid Parentheses.
Although it needs refactoring, I don't like its design.

```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stackList = []
        for bracket in s:
            #print(stackList)
            #print(bracket)
            if bracket == '(' or bracket == '{' or bracket == '[':
                stackList.append(bracket)
            elif len(stackList) == 0:
                return False
            elif bracket == ')' and stackList[-1] == '(':
                stackList.pop()
            elif bracket == ']' and stackList[-1] == '[':
                stackList.pop()
            elif bracket == '}' and stackList[-1] == '{':
                stackList.pop()
            else:
                return False
        
        return len(stackList)==0
                    
                
```
