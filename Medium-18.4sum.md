## Problem

https://leetcode.com/problems/4sum/

## Problem Description

```
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:

0 <= a, b, c, d < n
a, b, c, and d are distinct.
nums[a] + nums[b] + nums[c] + nums[d] == target
You may return the answer in any order.


Example 1:

Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        if (nums == null || nums.length < 4) return new ArrayList<>();
        
        Arrays.sort(nums);
        HashSet<List<Integer>> ans = new HashSet<>();
        
        for (int i = 0; i < nums.length - 3; i++) {
            for (int j = i + 1; j < nums.length - 2; j++) {
                int twoSumTarget = target - nums[i] - nums[j];
                HashSet<Integer> set = new HashSet<>();
                for (int k = j + 1; k < nums.length; k++) {
                    if (set.contains(twoSumTarget - nums[k])) {
                        ans.add(Arrays.asList(nums[i], nums[j], twoSumTarget - nums[k], nums[k]));
                    }
                    set.add(nums[k]);
                }
            }
        }
        
        return new ArrayList<>(ans);
    }
}
```
