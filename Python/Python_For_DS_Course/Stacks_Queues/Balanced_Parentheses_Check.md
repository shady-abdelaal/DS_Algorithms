Balanced Parentheses Check
Problem Statement
Given a string of opening and closing parentheses, check whether it’s balanced. We have 3 types of parentheses: round brackets: (), square brackets: [], and curly brackets: {}. Assume that the string doesn’t contain any other character than these, no spaces words or numbers. As a reminder, balanced parentheses require every opening parenthesis to be closed in the reverse order opened. For example ‘([])’ is balanced but ‘([)]’ is not.
You can assume the input string has no spaces.


#Solution
```python
def balance_check(s):
    shapes = {'[':']', '(':')', '{':'}'}
    stack = []
    for char in s:
        if char in shapes.keys():
            stack.append(char)
        elif char in shapes.values():
            if len(stack) == 0: # Edge case check, that the string starts with a closed paranthesis, or the start of a set is a closed paranthesis
                return False
            elif char == shapes[stack[-1]]:
                stack.pop()
            else:
                return False
            
    return stack==[]
```