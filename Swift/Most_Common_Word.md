https://leetcode.com/problems/most-common-word/

```swift
class Solution {
    func mostCommonWord(_ paragraph: String, _ banned: [String]) -> String {
        var counts: [String:Int] = [:]
        let components =  paragraph.split { !$0.isLetter }
        for component in components {
            let word = component.lowercased()
            if banned.contains(word) == false {
              counts[word, default: 0] += 1  
            }   
        }
        let sortedCounts = counts.sorted { $0.value > $1.value }
        return sortedCounts[0].key    
    }
}

```
