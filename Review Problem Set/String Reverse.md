There are few variations of this question, we will discuss the solutions of different variants in this file.

## Swap Input String
Here, there is no restriction on the space, you can take up more space if needed. Also, the input is a string.
### Solution
It is important to note that we can't do the operation in string, because strings are immutable in python, which means that if you did this:
```python
for c in inputString:
  outputString = c + outputString
```

Then complexity is `O(n^2)`, because at each iteration you have to re-write all the characters again in order to pre-pend to it.
The solution is to shift to a mutable object, nothing is better than a list in that matter in python.
So we first have to convert the input string into a list and then prepend to it and only after finishing, we can convert the list back to a string using `join()`

```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        
        stringList = list(s)
        reversedList = []
        for c in stringList:
            reversedList.insert(0,c)
        
        reversedList = ''.join(reversedList)
        return reversedList 
```

## Swap Input List in Place
In this variation of the problem, the input is given as a list of string characters, and the requirement is to do the reversing *in place* without consuming any extra space.
https://leetcode.com/problems/reverse-string/submissions/

### Solution
```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        
        swapIndex = len(s) - 1
        reversedList = []
        
        for i in range(len(s)/2):
            temp = s[i]
            s[i] = s[swapIndex]
            s[swapIndex] = temp
            swapIndex -= 1
        return reversedList
    
```
