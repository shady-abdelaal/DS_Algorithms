# String Compression

## Problem

Given a string in the form 'AAAABBBBCCCCCDDEEEE' compress it to become 'A4B4C5D2E4'. For this problem, you can falsely "compress" strings of single or double letters. For instance, it is okay for 'AAB' to return 'A2B1' even though this technically takes more space. 

The function should also be case sensitive, so that a string 'AAAaaa' returns 'A3a3'.


## Solution
```python
def compress(s):
    length = len(s)
    if length == 0:
        return ''
    elif length == 1:
        return s[0]


    compressedList = []
    compressedList.append(s[0])
    localCount = 1
    
    for i in range(1, len(s)):
        if (s[i] != s[i-1]):
            compressedList.append(str(localCount))
            compressedList.append(s[i])
            localCount = 1
    
            
        else:
            localCount += 1
            
            

    compressedList.append(str(localCount))
       
    return ''.join(compressedList)
```