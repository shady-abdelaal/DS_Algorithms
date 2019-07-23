# LeetCode Problem (Ransom Note)
https://leetcode.com/problems/ransom-note/

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

Note:
You may assume that both strings contain only lowercase letters.

canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true

**My Solution:**
``` python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        note_list = list(ransomNote)
        magazine_list = list(magazine)
        #print(note_list)
        for character in note_list:
            if character in magazine_list:
                magazine_list.remove(character)
            else:
                return False
            
        return True
```
The solution scored faster than 86.57% of python solutions.
The key to the better performance is converting the strings to list. The proble here would require you to remove the character from the magazine once
you find it. If that is performed on strings, this means bad performance. Because strings are immutable, so modifying them (by slicing, removing ,..ect)
would be handled internally by destroying the old copy and creating a totally new string. Which is a lot of work leading to a bad performance.

It is always a good practice in python to convert the strings into a list in case you intend to perform several mutating operations on it. 
And if the problem at hand requires you to convert it back to a string at the end, you can always use `join()` function to convert it back to a string.
