Source: Python for Data Structure, Algorithm and Interviews:

# Problem
Given an integer array, output the number of the * *unique ** pairs that sum up to a specific value k.
So the input:
pair_sum([1,3,2,2],4)
would return 2 pairs:
 (1,3)
 (2,2)
 
 # Solution
 
```python
def pair_sum(arr,k):
    counter = 0
    lookup = set()
    for num in arr:
        if k-num in lookup:
            counter+=1
        else:
            lookup.add(num)
    return counter
```

# Follow Up:
Change this logic to return the actual sets instead of just the count

```python
def pair_sum(arr,k):
    counter = 0
    lookup = set()
    output = set()
    for num in arr:
        target = k-num
        if target in lookup:
            counter+=1
            output.add( (min(num,target), max(num,target)) )
        else:
            lookup.add(num)

    return output
    
```
