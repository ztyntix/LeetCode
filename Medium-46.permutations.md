## Problem

https://leetcode.com/problems/permutations/

## Problem Description

```
Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

 

Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        
        permuteList(ans, new ArrayList<Integer>(), nums);
        return ans;
    }
    
    private void permuteList(List<List<Integer>> ans, List<Integer> res, int[] nums) {
        if (res.size() >= nums.length) {
            ans.add(new ArrayList<>(res));
            return;
        }
        
        for (int i = 0; i < nums.length; i++) {
            if (res.contains(nums[i])) continue;
            res.add(nums[i]);
            permuteList(ans, res, nums);
            res.remove(res.size() - 1);
        }
    }
}
```
