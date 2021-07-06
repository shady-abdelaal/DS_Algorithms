https://leetcode.com/problems/merge-two-sorted-lists/


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummy = ListNode()
        currentNode = dummy
        
        while l1 and l2:
            if l1.val < l2.val:
                currentNode.next = l1
                l1 = l1.next
                
            else:
                currentNode.next = l2
                l2 = l2.next
            
            currentNode = currentNode.next
            
                
        if l1:
            currentNode.next = l1
            
        if l2:
            currentNode.next = l2
            
        return dummy.next
```
