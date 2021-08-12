## Problem

https://leetcode.com/problems/maximum-subarray/

## Problem Description

```
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

 

Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        
        int sum = 0, max = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            sum = Math.max(sum + nums[i], nums[i]);
            max = Math.max(sum, max);
        }
        
        return max;
    }
}
```
