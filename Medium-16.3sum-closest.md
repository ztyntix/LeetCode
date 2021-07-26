## Problem

https://leetcode.com/problems/3sum-closest/

## Problem Description

```
Given an array nums of n integers and an integer target, find three integers in nums such that the sum is closest to target. Return the sum of the three integers. You may assume that each input would have exactly one solution.


Example 1:

Input: nums = [-1,2,1,-4], target = 1
Output: 2
Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        if (nums == null || nums.length < 3) return 0;
        Arrays.sort(nums);
        
        int ans = nums[0] + nums[1] + nums[2];
        for (int i = 0; i < nums.length - 2; i++) {
            int left = i + 1, right = nums.length - 1;
            int subTarget = target - nums[i];
            
            while (left < right) {
                int sum = nums[left] + nums[right];
                if (Math.abs(target - ans) > Math.abs(target - sum - nums[i])) {
                    ans = sum + nums[i];
                }
                if (sum < subTarget) left++;
                else right--;
            }
        }
        return ans;
    }
}
```
