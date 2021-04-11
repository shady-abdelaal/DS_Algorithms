https://leetcode.com/problems/pacific-atlantic-water-flow


```python
class Solution(object):
    def pacificAtlantic(self, heights):
        """
        :type heights: List[List[int]]
        :rtype: List[List[int]]
        """
        
        if not heights or not heights[0]:
            return []
        
        num_rows , num_columns = len(heights), len(heights[0])
        
        pacific_ocean = deque()
        atlantic_ocean = deque()
        
        for i in range(num_rows):
            pacific_ocean.append((i,0))
            atlantic_ocean.append((i, num_columns - 1))
        
        for j in range(num_columns):
            pacific_ocean.append((0,j))
            atlantic_ocean.append((num_rows - 1, j))
        
        def bfs(queue):
            reachable = set()
            while queue:
                (row, col) = queue.popleft()
                reachable.add((row,col))

                for (x,y) in [(1,0), (0,1), (-1,0), (0,-1)]:
                    new_row, new_column = row + x, col + y

                    if new_row <0 or new_row >= num_rows or new_column<0 or new_column>=num_columns:
                        continue

                    if (new_row, new_column) in reachable:
                        continue

                    if heights[new_row][new_column] < heights[row][col]:
                        continue


                    queue.append((new_row,new_column))
            return reachable
                
        pacific_reachable = bfs(pacific_ocean)
        atlantic_reachable = bfs(atlantic_ocean)

        return list(pacific_reachable.intersection(atlantic_reachable))
```
