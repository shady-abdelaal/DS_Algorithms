# Solving Counting Problems with Python

In this tutorial, we are going to discuss some tips and tricks to solving counting problems with Python. First through the basic, standard python data structures
and then with the more advanced counter module.

Counting problems are a category of "problem solving" where you are faced with the problem where you need to keep track of the count of different stream of data. 
For instance, let's have a look at this problem: https://leetcode.com/problems/sort-characters-by-frequency/ . Where, given a string, we need to
sort it in decreasing order based on the frequency of characters. For example: Input: "tree" , Output: "eert".
Another example: given a file which represents an internet browser history for the last month. Return the 10 most visited websites sorted along with the number of visits
for each.

Now, we are going to discuss the ways used to solve similar problemd with 2 possible techniques.

** Classical Approach - Dictionary:
Python dictionary is a powerful tool, any developer using python would definitely need to master their use as they can give you an incredible/fast ways to keep track of data related to a key. 
For more info about dictionaries:

Let's take the first problem we introduced in the previous section and see how can we solve it with dictionaries.
First, the counting:

```python
def counting_string(input_string):
    counting_dictionary = {}
    for element in input_string:
        if element in counting_dictionary.keys():
            counting_dictionary[element] += 1
        else:
            counting_dictionary[element] = 1

    return counting_dictionary
```

This function would return back a dictionary, with the 'character' as a key and the number of appearances as the value. 
Try it with the input "tree" -> Output dictionary: {'t': 1, 'r': 1, 'e': 2}

Or, we can implement the same behavior but with a more elegant, pythonic way. Using dictionary.get()

```python
def counting_string(input_string):
    counting_dictionary = {}
    for element in input_string:
        counting_dictionary[element] = counting_dictionary.get(element, 0) + 1  # get will return the value if the key exists, else, it will return 0
        
    return counting_dictionary
```
