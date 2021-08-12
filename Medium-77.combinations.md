## Problem

https://leetcode.com/problems/combinations/

## Problem Description

```

Given two integers n and k, return all possible combinations of k numbers out of the range [1, n].

You may return the answer in any order.

 

Example 1:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
```

## Code

-Support Language: JAVA

```JAVA

class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> ans = new ArrayList<>();
        
        combineCompute(ans, new ArrayList<Integer>(), n, k, 1);
        return ans;
    }
    
    private void combineCompute(List<List<Integer>> ans, List<Integer> temp, int n, int k, int index) {
        if (temp.size() == k) {
            ans.add(new ArrayList<>(temp));
            return;
        }
        
        for (int i = index; i <= n; i++) {
            temp.add(i);
            combineCompute(ans, temp, n, k, i + 1);
            temp.remove(temp.size() - 1);
        }
    }
}
```
