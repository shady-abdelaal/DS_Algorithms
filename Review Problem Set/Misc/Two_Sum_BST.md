https://leetcode.com/problems/two-sum-iv-input-is-a-bst/

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def findTarget(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: bool
        """
        queue = []
        queue.append(root)
        uniqueSet = set()
        
        while queue:
            current = queue.pop(0)
            
            if current.val in uniqueSet:
                return True
            else:
                uniqueSet.add(k - current.val) 
            
            if current.left:
                queue.append(current.left)
                
            if current.right:
                queue.append(current.right)
                
        return False
```
