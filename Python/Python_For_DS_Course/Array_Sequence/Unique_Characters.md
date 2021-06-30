Unique Characters in String

## Problem
Given a string,determine if it is compreised of all unique characters. For example, the string 'abcde' has all unique characters and should return True. The string 'aabcde' contains duplicate characters and should return false.


## Discussion

In most unique elements problems, we have to first think of a solution using `set()` . Because it is a unique python data structure that doesn't allow duplication.
## Easy 1 Line Solution:

```python
def uni_char(s):
    return len(set(s)) == len(list(s))
```


## More manual Solution:
```python
def uni_char2(s):
    uniqueSet = set()
    
    for char in s:
        if char in uniqueSet:
            return False
        else:
            uniqueSet.add(char)
        
    return True
```