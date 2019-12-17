### [LC 374](https://leetcode.com/problems/guess-number-higher-or-lower/)

Better expression for mid-value
```java
int mid = low + (high - low) / 2;
```

instead of 
```java
int mid = (low + high) / 2;// may cause overflow
```