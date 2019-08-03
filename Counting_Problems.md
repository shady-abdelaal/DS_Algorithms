# Solving Counting Problems with Python

In this tutorial, we are going to discuss some tips and tricks to solving counting problems with Python. First through the basic, standard python data structures
and then with the more advanced counter module.

Counting problems are a category of "problem solving" where you are faced with the problem where you need to keep track of the count of different stream of data. 
For instance, let's have a look at this problem: https://leetcode.com/problems/sort-characters-by-frequency/ . Where, given a string, we need to
sort it in decreasing order based on the frequency of characters. For example: Input: "tree" , Output: "eert".
Another example: given a file which represents an internet browser history for the last month. Return the 10 most visited websites sorted along with the number of visits
for each.

Now, we are going to discuss the ways used to solve similar problemd with 2 possible techniques.

## Classical Approach - Dictionary:
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
        counting_dictionary[element] = counting_dictionary.get(element, 0) + 1  
        # get will return the value if the key exists, else, it will return 0
        
    return counting_dictionary
```

Now that we have the detailed count of the string's characters, we want to sort them in descending order. 
Dictoniaries in python have no specific order, unlike list & tuple, we can't "sort" a dictionary because the order is meaningless. Dictionaries are hash maps, which reach the value based on the input key and nothing more. (Ant that's what makes searching in a dictionary O(1), but that's a topic for another article).

So, we will have to use the "items()" method of dictionary in order to return the keys and values to a tuple that we can then sort.

``` sorted_tuples = sorted(counting_dictoniary.items() ,  key=lambda x: x[1], reverse = True) ```
If tried on the example we have, then: input: {'t': 1, 'r': 1, 'e': 2} -> Output is: [('e', 2), ('t', 1), ('r', 1)]

Now, we have the characters, each with its frequency and also sorted in a descending order. We now have to assemble the output string based on these tuples:
```
for i in sorted_tuples:
        res += i[0]*i[1]

```

**The whole code would be:

```python
def sort_string(input_string):
    counting_dictionary = {}
    for element in input_string:
        counting_dictionary[element] = counting_dictionary.get(element, 0) + 1
        
    return counting_dictionary



if __name__ == '__main__':
    input_string = "tree"
    detailed_dict = sort_string_2(input_string)
    sorted_tuples = sorted(detailed_dict.items() ,  key=lambda x: x[1], reverse = True)
    res = ""
    for i in sorted_tuples:
        res += i[0]*i[1]

    print(res)
```
