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
