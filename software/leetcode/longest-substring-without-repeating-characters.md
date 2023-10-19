## Longest Substring Without Repeating Characters

The objective of this problem is to find the length the longest substring inside a larger string that has no repeating characters. For example, the in the string "abcabcdaab" the longest substring with no repeating characters is "abcd".

### Solution: Brute force
The brute force approach for this problem would involve using two pointers to generate all possible substrings and then detecting duplicates in each substring. Checking a substring for duplicates is an O(n) operation. Generating every possible substring is an O(n^2) operation. Therefore the brute force approach would be O(n^3).

### Solution: Sliding window with hash set
In this solution, instead of brute forcing every substring, we will use two indices to form a sliding window. We will also use a hash set to keep track of which characters have been seen in the current sliding window.

```
while the end pointer is less than the length of the input string
    if the character at the end pointer is not in the hash set
        add it to the hash set
        if the size of the hash set is bigger than the current max
            set the max to the size of the hash set
        increment the end pointer
    otherwise
        remove the character at the start pointer from the hash set
        increment the start pointer
return the max
```

Since the end pointer is only updated when the current character is not in the hash set, the algorithm will effectively remove all characters from the hash set up to and including the character in which the duplicate was detected. Once that character is removed, the end pointer will start updating again until it hits another repeat.