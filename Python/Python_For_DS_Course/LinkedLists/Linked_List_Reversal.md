Linked List Reversal
Problem
Write a function to reverse a Linked List in place. The function will take in the head of the list as input and return the new head of the list.
You are given the example Linked List Node class:


```python
class Node(object):
    
    def __init__(self,value):
        
        self.value = value
        self.nextnode = None


def reverse(head):
    current = head
    previous = None
    nextNode = None
    
    while current:
        nextNode = current.nextnode
        current.nextnode = previous

        previous = current
        current = nextNode
    
    return previous
```