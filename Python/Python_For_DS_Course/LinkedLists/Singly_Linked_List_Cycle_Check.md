Singly Linked List Cycle Check
Problem
Given a singly linked list, write a function which takes in the first node in a singly linked list and returns a boolean indicating if the linked list contains a "cycle".
A cycle is when a node's next point actually points back to a previous node in the list. This is also sometimes known as a circularly linked list.
You've been given the Linked List Node class code:

```python
class Node(object):
    
    def __init__(self,value):
        
        self.value = value
        self.nextnode = None


def cycle_check(node):
    slowPointer = node
    fastPointer = node
    
    while slowPointer.nextnode and fastPointer.nextnode:
        slowPointer = slowPointer.nextnode 
        fastPointer = fastPointer.nextnode.nextnode
        
        if slowPointer == fastPointer:
            return True
        
    return False

```