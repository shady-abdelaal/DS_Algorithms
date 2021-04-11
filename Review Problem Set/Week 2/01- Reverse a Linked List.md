https://leetcode.com/problems/reverse-linked-list/submissions/


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        prev = None
        current = head
        while current is not None:
            nextNode = current.next
            current.next = prev
            prev = current
            current = nextNode
            
        head = prev
        return head
```
