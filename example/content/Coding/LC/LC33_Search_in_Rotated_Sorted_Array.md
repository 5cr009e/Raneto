### [LC33 20191214](https://leetcode.com/problems/search-in-rotated-sorted-array/)
Search a sorted array with unknown pivot point in O(log n)
Related:[LC35 Search insert position](https://leetcode.com/problems/search-insert-position/)

O(log(n))=> Binary Search, key point is finding out the pruning condition for subsequence.

If the original start point is in a subsequence, we have inversion: low > high in this subsequence because of pivot, e.g. [1,2,3,4]->[4,1,2,3], which is also true for any subsquence of it.

In detail, for low < mid and mid < high, ordered, tgt>=mid for right and tgt < mid for left.
For low < mid but mid > high, left ordered, tgt < mid for left and else for right.
For low > mid but mid < high, right ordered, tgt >= mid for right and else for left.