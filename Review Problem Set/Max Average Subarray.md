https://leetcode.com/problems/maximum-average-subarray-i/

Should be easy, using the sliding window technique.

```python
best = now = sum(nums[:k])
        for i in range(k,len(nums)):
            now += nums[i] - nums[i-k]
            best = max(best,now)
        k = float(k)
        return best/k
```
