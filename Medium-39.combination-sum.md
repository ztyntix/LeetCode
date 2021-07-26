## Problem

https://leetcode.com/problems/combination-sum/

## Problem Description

```
Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.
 

Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        Arrays.sort(candidates);
        List<List<Integer>> ans = new ArrayList<>();
        
        combination(ans, new ArrayList<>(), target, candidates, 0);
        return ans;
    }
    
    private void combination(List<List<Integer>> ans, List<Integer> res, int target, int[] candidates, int index) {
        if (index >= candidates.length || target < 0) return;
        
        if (target == 0) {
            ans.add(new ArrayList<>(res));
            return;
        }
        
        for(int i = index; i < candidates.length; i++) {
            res.add(candidates[i]);
            combination(ans, res, target - candidates[i], candidates, i);
            res.remove(res.size() - 1);
        }
    }
}
```
