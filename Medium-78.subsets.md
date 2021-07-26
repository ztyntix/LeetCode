## Problem

https://leetcode.com/problems/subsets/

## Problem Description

```
Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

 

Example 1:

Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        
        subsetsCompute(nums, new ArrayList<Integer>(), ans, 0);
        return ans;
    }
    
    private void subsetsCompute(int[] nums, List<Integer> temp, List<List<Integer>> ans, int index) {
        ans.add(new ArrayList<>(temp));
        
        for (int i = index; i < nums.length; i++) {
            temp.add(nums[i]);
            subsetsCompute(nums, temp, ans, i + 1);
            temp.remove(temp.size() - 1);
        }
    }
}
```
