
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/submissions/

```
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        import numpy as np
        minValue = np.inf
        maxProfit = 0
        for price in prices:
            if price < minValue:
                minValue = price
                              
            if price - minValue > maxProfit:
                maxProfit = price - minValue
    
            
        return maxProfit
            
            
```
