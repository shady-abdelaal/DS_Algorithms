
# Sentence Reversal
Problem
Given a string of words, reverse all the words. For example:
Given:
'This is the best'
Return:
'best the is This'
As part of this exercise you should remove all leading and trailing whitespace. So that inputs such as:
'  space here'  and 'space here      '
both become:
'here space'



Straight forward solution, using python build in functions:

```python
def rev_word(s):
    wordsList = s.split()
    wordsList.reverse()
    print(wordsList)
    reversedSentence = ' '.join(wordsList)
    
    return reversedSentence
```

However, in a real interview setting, that solution is not prefered.

Manual algorithm:
```python
def rev_word2(s):
    wordsList = []
    length = len(s)
    i = 0
    spaces = [' ']
    
    while i<length:
        if s[i] not in spaces:
            start_index = i
            
            while i < length and s[i] not in spaces:
                i += 1 

            wordsList.append(s[start_index:i])
        
        i += 1
    
    return ' '.join(reversed(wordsList))
```

Going further and doing the reversal manually as well:

```python
def rev_word3(s):
    wordsList = []
    length = len(s)
    i = 0
    spaces = [' ']
    
    while i<length:
        if s[i] not in spaces:
            start_index = i
            
            while i < length and s[i] not in spaces:
                i += 1 

            wordsList.append(s[start_index:i])
        
        i += 1
    
    reversedList = []
    j = len(wordsList) - 1
    while j >= 0:
        reversedList.append(wordsList[j])
        j -= 1
        
    return ' '.join(reversedList)
```