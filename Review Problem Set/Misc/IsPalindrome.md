https://leetcode.com/problems/valid-palindrome/


Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

 

Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.


```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        normalizedCharList = []
        for char in s:
            if char.isalpha() or char.isnumeric():
                normalizedCharList.append(char.lower())
        
        for i in range(len(normalizedCharList)//2):    
            if normalizedCharList[i] == normalizedCharList[-i-1]:
                continue
            else:
                return False
            
        return True
```
