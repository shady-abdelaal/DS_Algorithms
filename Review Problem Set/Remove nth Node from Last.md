https://leetcode.com/problems/remove-nth-node-from-end-of-list/submissions/

2 pointers approach, performed very well: 

Runtime: 16 ms, faster than 90.21% of Python online submissions for Remove Nth Node From End of List.
Memory Usage: 13.2 MB, less than 93.07% of Python online submissions for Remove Nth Node From End of List.

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        second = head
        for j in range(n):
            second = second.next
         
        if not head.next: 
            head = None
            return head
        
        first = head
        while second:
            second = second.next
            previous = first
            first = first.next
        
        if first == head:
            return head.next
        
        previous.next = previous.next.next
        return head
```
