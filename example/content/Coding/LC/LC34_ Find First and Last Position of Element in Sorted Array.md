### [LC34 20191214](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

O(log n) => Binary search

- pruning condition
  - target<*m: keep left
  - target > *m: keep right
  - target = *m: check *(m-1) or *(m+1)
- stop condition
  - for left: *(m) = tgt && *(m-1) = tgt 
  - for right: *(m) = tgt && *(m-1) = tgt

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        
        int[] result = {-1, -1};
        if (nums.length == 0){
            return result;
        }    
        int start = findPos(nums, target, true);
        int end = findPos(nums, target, false);
        if (nums[start]==target && nums[end]==target){
            result[0] = start;
            result[1] = end;
        }
        return result;
        
    }
    
    int findPos(int[] nums, int target, boolean left){
        int l = 0;
        int r = nums.length - 1;

        while(l < r){
            int m = l + (r - l) / 2;
            if(target > nums[m]){
                l = m + 1;
            }else if (target < nums[m]){
                r = m;
            // from here, target = nums[m]
            }else if(left)
                    {
                        if (m > 0 && target > nums[m-1]) {return m;}
                        else { r = m; }
                    }else{
                        if(m < nums.length && target < nums[m+1]){return m;}
                        else { l = m+1; }
                
                    } 
        }
        return l;
    }
}
```

