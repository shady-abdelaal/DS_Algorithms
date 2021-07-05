https://leetcode.com/problems/intersection-of-two-linked-lists/


Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        # Can use only 1 unique set, because there is a guarantee that there are no cycles
        # If that was not guaranteed, then we must have had a separate sets for A and B
        uniqueSet = set() 
        
        intersection = None
        currentA = headA
        currentB = headB
        
        while currentA:
            if currentA in uniqueSet:
                return currentA
            
            else:
                uniqueSet.add(currentA)
                currentA = currentA.next 
                
        while currentB:
            if currentB in uniqueSet:
                return currentB
            else:
                uniqueSet.add(currentB)
                currentB = currentB.next
                
        
        return intersection
```
