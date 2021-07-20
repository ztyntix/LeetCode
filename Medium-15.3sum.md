## Problem

https://leetcode.com/problems/3sum/

## Problem Description

```
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.


Example 1:

Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if (nums == null || nums.length < 3) return new ArrayList<>();
        Arrays.sort(nums);
        
        HashSet<List<Integer>> ans = new HashSet<>();
        for (int i = 0; i < nums.length - 2; i++) {
            int target = -1 * nums[i];
            HashSet<Integer> set = new HashSet<>();
            for (int j = i + 1; j < nums.length; j++) {
                if (set.contains(target - nums[j])) {
                    ans.add(Arrays.asList(nums[i], target - nums[j], nums[j]));
                }
                set.add(nums[j]);
            }
        }
        return new ArrayList<>(ans);
    }
}
```
