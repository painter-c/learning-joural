## Longest Palindrome Substring (Leetcode 5)

The objective of this problem is to determine the longest palindrome substring inside of a parent string. A palindrome is a string that is equivalent to its own inverse. The strings "AABB", "ABCBA", and "AA" are all examples of palindromes.

#### Examples
- The largest palindrome in the string "xyzacazwk" is "zacaz"
- The largest palindrome in the string "tyyuuuvx" is "yyuu"

### Solution 1: Brute force
This problem could be solved by checking every possible substring to be a palindrome. This can be achieved with two indices that correspond to the left and right ends of the substring. An outer loop would iterate over the left index and an inner loop would iterate the right index from the end of the string until the left index. At each step of this loop you check if the substring from the left index to the right index is a palindrome; if it is the longest one seen yet then record it.

#### Problems
The brute force solution is O(n^3). This is because the outer and inner loops result in n^2 operations and checking if a substring is a palindrome takes n operations; for a total of n^3. The main cause of this poor performance is due to checking for palindromes from the outside in. Consider a small 3 character palindrome inside a string of 1000 characters. Since palindrome checking is a symmetric operation, there are roughly 500 pairs of indices with the same center as the palindrome. In the brute force algorithm, each of these indices are checked while the only possible palindrome is the small 3 character one in its center. This results in a lot of wasted computation.

### Solution 2: Optimized
Instead of checking each of the 500 indices mentioned in the brute force example, searching for palindromes from the inside out is more efficient. Now to find each palindrome with a given center, it only takes the minimum amount of operations to determine if it is a palindrome rather that calculating many redundant pairs of indices.

In this solution, we iterate over each position in the input string; this position corresponds to the center of a possible palindrome. Then in an inner loop we expand a pair of indices outward; the substring is a palindrome as long as the characters at both indices are equal. At each step we check if we need to update the longest palindrome. In this solution the outer loop runs n times, the inner loop is an O(n) operation, and therefore the complexity of this solution is O(n^2).

There is one final edge case that must be considered, which arises due to the fact that palindromes can be of either an odd or even length. In the above algorithm we consider the outer loop to correspond to the center of a possible palindrome, however an even length palindrome will not have a center. It is thus necessary to check both even and odd length palindromes with a slighly different algorithm. The combination of these two edge cases constitute the final solution.