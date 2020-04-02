# Code
``` python
class Solution(object):
    def isHappy(self, n):
        """
        :type n: int
        :rtype: bool
        """
        visited_numbers = set()
        while n not in visited_numbers:
            visited_numbers.add(n)
            n = sum(int(digit)**2 for digit in str(n))
            if n == 1:
                return True
        return False
```
