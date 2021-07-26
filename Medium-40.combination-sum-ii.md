## Problem

https://leetcode.com/problems/combination-sum-ii/

## Problem Description

```
Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.


Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        
        Arrays.sort(candidates);
        combinationCompute(ans, new ArrayList<>(), candidates, target, 0);
        return ans;
    }
    
    private void combinationCompute(List<List<Integer>> ans, List<Integer> temp, int[] candidates, int target, int index) {
        if (target < 0) return;
        
        if (target == 0) {
            ans.add(new ArrayList<>(temp));
            return;
        }
        
        for (int i = index; i < candidates.length; i++) {
            if (i > index && candidates[i] == candidates[i - 1]) continue;
            temp.add(candidates[i]);
            combinationCompute(ans, temp, candidates, target - candidates[i], i + 1);
            temp.remove(temp.size() - 1);
        }
    }
}
```
