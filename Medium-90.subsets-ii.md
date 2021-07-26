## Problem

https://leetcode.com/problems/subsets-ii/

## Problem Description

```
Given an integer array nums that may contain duplicates, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

 

Example 1:

Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ans = new ArrayList<>();
        
        subsetsCompute(ans, new ArrayList<>(), nums, 0);
        return ans;
    }
    
    private void subsetsCompute(List<List<Integer>> ans, List<Integer> temp, int[] nums, int index) {
        ans.add(new ArrayList<>(temp));
        
        for (int i = index; i < nums.length; i++) {
            if (i > index && nums[i] == nums[i - 1]) continue;
            temp.add(nums[i]);
            subsetsCompute(ans, temp, nums, i + 1);
            temp.remove(temp.size() - 1);
        }
    }
}
```
