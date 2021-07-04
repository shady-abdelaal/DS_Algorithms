Linked List Nth to Last Node
Problem Statement
Write a function that takes a head node and an integer value n and then returns the nth to last node in the linked list. For example, given:


```python
class Node:

    def __init__(self, value):
        self.value = value
        self.nextnode  = None


def nth_to_last_node(n, head):
    node = head
    current = head

    for i in range(n-1):
        node = node.nextnode
        
        if not node.nextnode:
            raise LookupError('Error: n is larger than the linked list')

    while node.nextnode:
        current = current.nextnode
        node = node.nextnode
        
    return current
```