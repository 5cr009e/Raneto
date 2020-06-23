### [LC 162 Find Peak Element](https://cspiration.com/leetcodeClassification#10311)

Binary Search

Key point is problem definition, peak point at i is equivalent to liner search n[i]>n[i+1].

BS solution:
The rising direction must have at least one peak since n[-1]=n[n]=-infinity. So search from the middle, only keep the rising side.
