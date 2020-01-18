This problem is from Swift course on udemy. 
Since I am still new to swift, I thought I should start with the basics, and what is better than counting problems?! Counting problems touch on the basics since it deals with strings, lists and dictionaries and moreover, operating on these dictionaries like sorting. So this problem is a good start for a swift beginner to get things going.

**The problem statement is:**
***Write a function that takes in any text, and counts how many words there are in total and list the words from the most used to the least. Dealing with the text as case insensitive.***

## The Logic:
Now let's break the problem statement into detailed steps and tackle each one by one.
1. Slice the text by the spaces to get a list of words.
2. Count the words.
3. Sort the words and return them from the most used to the least.

Let's get into details and discuss each step of the algorithm along with its suitable data strucutre.

### Slicing:
In this step, all we need is to extract the 'words' from a block of text (string). How? Through 'slicing' by the space delimiter. And what is better to use than an array (or list) to store the output words. So, we can make use of `components()` function to do the task:

```swift
var full_text = "This is a test string. Here, I am testing the program with a test string called full_text. How do you think we will do on this test ?"
full_text = full_text.lowercased()
let full_text_array = full_text.components(separatedBy: " ")
```

### Counting:
In this step, we need to count how many times each word appeared, in this type of problems, when you need to store some info about a specific element, and at the same time you don't care about the order of this element. Then the most suitable data strucutre is a dictionary (or a hash map). A dictionary `words_count: [String: Int]` is perfect for storing such information. The key here is the word itself (populated from the list) and the value is how many time that word appeared in the list of words.
```swift
var words_count: [String: Int] = [:]

for word in full_text_array {
  if  let val = words_count[word] {
    words_count[word] = val + 1
  }
  else {
    words_count[word] = 1
  }
}
```

### Sorting:
At this stage, we have a dictionary which contains all the words as keys and each word's count as the value, that's great. Now, we have to sort this in a descinding order. Swift has a function called `sorted(by: byValue)` which can operate on a dictinary, it takes a parameter `by`. Where you got to chose a custom boolean where the sorting would follow. Literally any sorting can be done within a boolean and then passed to `sorted()` function to be applied to the whole dictionary. This method comes in handy with way more complicated sorts (but that's a story for another tutorial), but here, all we need to do is set the boolean to true if `eleme1` is bigger than `elemen2` . Here is the code:
```swift
let byValue = {
  (elem1:(key: String, val: Int), elem2:(key: String, val: Int))->Bool in
  if elem1.val > elem2.val {
    return true
  } else {
    return false
  }
}

let sortedDict = words_count.sorted(by: byValue)
```

And finally, printing out the result and we are done :) 



## Final Solution
Here is the full solution:


```swift
import Foundation
var full_text = "This is a test This is"
full_text = full_text.lowercased()
let full_text_array = full_text.components(separatedBy: " ")

var words_count: [String: Int] = [:]

for word in full_text_array {
  if  let val = words_count[word] {
    words_count[word] = val + 1
  }
  else {
    words_count[word] = 1
  }
}

let byValue = {
  (elem1:(key: String, val: Int), elem2:(key: String, val: Int))->Bool in
  if elem1.val > elem2.val {
    return true
  } else {
    return false
  }
}
let sortedDict = words_count.sorted(by: byValue)
 let no_of_words = words_count.count

print("\(no_of_words) Words")
var index_count = 1
for(key,value) in sortedDict {
  print("\(index_count). \(key) - \(value)")
  index_count += 1
}
```

## Summary:
In this short tutorial, we introduced the basic concepts of counting problems along with their implementation with Swift. `Slicing` which is an essential method when dealing with strings, then counting instances using the most suitable data structure; in this case that is the dictionary and finally sorting the dictionary based on the `value`. 
