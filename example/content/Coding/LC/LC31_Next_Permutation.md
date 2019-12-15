### [LC31 20191213](https://leetcode.com/problems/next-permutation/)

Related: [lexicographical order](https://en.wikipedia.org/wiki/Lexicographical_order), [permutation](https://leetcode.com/problems/permutations/)


Another interest algorithm for permutation generator: [Johnson and Trotter algorithm
](https://www.geeksforgeeks.org/johnson-trotter-algorithm/)

### Basic Idea
#### Solution 0
Brute Force: go through all permutations and find the minimal permutation that larger than the given one.
TC: O(n!)
SC: O(n)
#### Solution 1
Find the last ascending sequence from the end, let's say a[i-1] and a[i], then after them the sequence would be descending. Pick out the largest number grater than a[i-1] among all the numbers after them, say a[j], swap a[j-1] and a[j] (that's generate permutations), but we want the new sequence be a minimum one that greater than the given one, so find the minimum subsequence besides the two numbers, which is a ascending sequence, so we invert all the other numbers.   