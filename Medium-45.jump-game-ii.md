## Problem

https://leetcode.com/problems/jump-game-ii/

## Problem Description

```
Given an array of non-negative integers nums, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

You can assume that you can always reach the last index.

 

Example 1:

Input: nums = [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

## Code

-Support Language: JAVA

```JAVA

class Solution {
    // The main idea is based on greedy.
    // Let's say the range of the current jump is [curBegin, curEnd], 
    // curFarthest is the farthest point that all points in [curBegin, curEnd] can reach. 
    // Once the current point reaches curEnd, then trigger another jump, and set the new curEnd with curFarthest...
    public int jump(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        
        int curLongest = 0, step = 0, lastEnd = 0;
        
        for (int i = 0; i < nums.length - 1; i++) {
            curLongest = Math.max(curLongest, i + nums[i]);
            if(i == lastEnd) {
                step++;
                lastEnd = curLongest;
            }
        }
        
        return step;
    }
}
```
