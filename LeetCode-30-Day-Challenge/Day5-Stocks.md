```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        transaction_stack = []
        profit = 0
        for i in range(0, len(prices)):
            if (i == len(prices) - 1):
                if len(transaction_stack) != 0:
                    profit = profit + prices[i] - transaction_stack[0]
            else:
                if prices[i+1] > prices[i]:
                    if len(transaction_stack) == 0:
                        transaction_stack.append(prices[i])
                    else:
                        pass
                        
                if prices[i+1] < prices[i]:
                    if len(transaction_stack) != 0:
                        profit = profit + prices[i] - transaction_stack[0]
                        del transaction_stack[0] # Sell
                    else:
                        pass
                else:
                    pass
        return profit
               
```
