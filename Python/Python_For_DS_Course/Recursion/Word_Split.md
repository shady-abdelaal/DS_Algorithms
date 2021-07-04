#Problem 3
Note, this is a more advanced problem than the previous two! It aso has a lot of variation possibilities and we're ignoring strict requirements here.
Create a function called word_split() which takes in a string phrase and a set list_of_words. The function will then determine if it is possible to split the string in a way in which words can be made from the list of words. You can assume the phrase will only contain words found in the dictionary if it is completely splittable.


Example
word_split('themanran',['the','ran','man'])
Output: ['the', 'man', 'ran']



```python
def word_split(phrase,list_of_words, output = None):
    
    if output is None:
        output = []
        
    for word in list_of_words:
        
        if phrase.startswith(word):
            output.append(word)
            return word_split(phrase[len(word):], list_of_words, output)
        
    return output
```