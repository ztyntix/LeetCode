## Problem

https://leetcode.com/problems/valid-sudoku/

## Problem Description

```
Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] ans = new int[] {-1, -1};
        if (nums == null || nums.length == 0) return ans;
        
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = (left + right) / 2;
            if (nums[mid] < target) left = mid + 1;
            else right = mid;
        }
        if (nums[left] != target) return ans;
        
        ans[0] = left;
        
        right = left;
        while(right < nums.length) {
            if (nums[right] == nums[left]) right++;
            else break;
        }
        ans[1] = right - 1;
        
        return ans;
    }
}
```
