## Problem

https://leetcode.com/problems/generate-parentheses/

## Problem Description

```
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

 

Example 1:

Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ans = new ArrayList<String>();
        dfs(n, 1, 1, "", ans);
        return ans;
    }
    
    private void dfs(int n, int left, int right, String res, List<String> ans) {
        if (res.length() == 2 * n) {
            ans.add(res);
            return;
        }
        if (left <= n) {
            dfs(n, left + 1, right, res + "(", ans);
        }
        
        if (right < left) {
            dfs(n, left, right + 1, res + ")", ans);
        }
    }
}
```
