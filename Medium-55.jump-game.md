## Problem

https://leetcode.com/problems/jump-game/

## Problem Description

```

Given an array of non-negative integers nums, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

 

Example 1:

Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.

```

## Code

-Support Language: JAVA

```JAVA

class Solution {
    public boolean canJump(int[] nums) {
        int len = nums.length;
        
        int longest = 0;
        for (int i = 0; i <= longest; i++) {
            // longest stores the longest index from current position
            if (longest >= len - 1) return true;
            longest = Math.max(i + nums[i], longest);
        }
        
        return longest >= len - 1;
    }
}
```
