This problem is from Swift course on udemy. 
Since I am still new to swift, I thought I should start with the basics, and what is better than counting problems?! Counting problems touch on the basics since it deals with strings, lists and dictionaries and moreover, operating on these dictionaries like sorting. So this problem is a good start for a swift beginner to get things going.

The problem statement is:
Write a function that takes in any text, and counts how many words there are in total and list the words from the most used to the least. Dealing with the text as case insensitive.

## The Logic:
Now let's break the problem statement into detailed steps and tackle each one by one.
1. Slice the text by the spaces to get a list of words.
2. Count the words.
3. Sort the words and return them from the most used to the least.

### Slicing:

### Counting:

### Sorting:

## Final Solution


```swift
import Foundation
var full_text = "This is a test This is"
full_text = full_text.lowercased()
let full_text_array = full_text.components(separatedBy: " ")

var dictionary_count: [String: Int] = [:]

for word in full_text_array {
  if  let val = dictionary_count[word] {
    dictionary_count[word] = val + 1
  }
  else {
    dictionary_count[word] = 1
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
let sortedDict = dictionary_count.sorted(by: byValue)
 let no_of_words = dictionary_count.count

print("\(no_of_words) Words")
var index_count = 1
for(key,value) in sortedDict {
  print("\(index_count). \(key) - \(value)")
  index_count += 1
}
```
