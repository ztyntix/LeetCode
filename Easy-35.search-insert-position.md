## Problem

https://leetcode.com/problems/search-insert-position/

## Problem Description

```
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [1,3,5,6], target = 5
Output: 2
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int searchInsert(int[] nums, int target) {
        if (nums == null || nums.length == 0) return -1;
        
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (nums[mid] == target) return mid;
            
            if (nums[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        
        return left;
    }
        
}
```
