# Cracking the coding interview - chapter 1

String Compression: Implement a method to perform basic string compression using the counts
of repeated characters. For example, the string aabcccccaaa would become a2blc5a3. If the
"compressed" string would not become smaller than the original string, your method should return
the original string. You can assume the string has only uppercase and lowercase letters (a - z).



``` python
def string_compression(inputString):
    compressedString = ""
    consecutiveCount = 1
    for i in range(len(inputString)):
        if(i+1 >= len(inputString) or inputString[i] != inputString[i+1]):
            compressedString += inputString[i] +  str(consecutiveCount)
            consecutiveCount = 1
            
        else:
            consecutiveCount += 1
            
    
    if(len(compressedString) >= len(inputString)):
        return inputString
    
    return compressedString
        
def string_compression2(inputString):
    compressedString = []
    consecutiveCount = 1
    for i in range(len(inputString)):
        if(i+1 >= len(inputString) or inputString[i] != inputString[i+1]):
            compressedString.extend([inputString[i] ,  str(consecutiveCount)])
            consecutiveCount = 1
            
        else:
            consecutiveCount += 1
            

    return min(''.join(compressedString),inputString, key=len)
    
    
def main():
    answer = string_compression("aaassssfjff")
    print(answer)

    answer = string_compression("abcdefg")
    print(answer)


if __name__ == '__main__':
    main()
```
