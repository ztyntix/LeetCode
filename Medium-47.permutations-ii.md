## Problem

https://leetcode.com/problems/permutations-ii/

## Problem Description

```
Given a collection of numbers, nums, that might contain duplicates, return all possible unique permutations in any order.

 

Example 1:

Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        boolean[] used = new boolean[nums.length];
        
        Arrays.sort(nums);
        permuteList(ans, new ArrayList<Integer>(), nums, used);
        return ans;
    }
    
    private void permuteList(List<List<Integer>> ans, List<Integer> res, int[] nums, boolean[] used) {
        if (res.size() >= nums.length) {
            ans.add(new ArrayList<>(res));
            return;
        }
        
        for (int i = 0; i < nums.length; i++) {
            if (used[i] || i > 0 && nums[i] == nums[i - 1] && used[i - 1]) continue;
            res.add(nums[i]);
            used[i] = true;
            permuteList(ans, res, nums, used);
            res.remove(res.size() - 1);
            used[i] = false;
        }
    }
}
```
