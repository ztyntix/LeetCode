## Problem

https://leetcode.com/problems/minimum-path-sum/

## Problem Description

```
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

 

Example 1:


Input: grid = [[1,3,1],[1,5,1],[4,2,1]]
Output: 7
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int minPathSum(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        
        int[][] dp = new int[m][n];
        dp[0][0] = grid[0][0];
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0 && j == 0) continue;
                int left = j > 0 ? dp[i][j - 1] : Integer.MAX_VALUE;
                int up = i > 0 ? dp[i - 1][j] : Integer.MAX_VALUE;
                dp[i][j] = Math.min(left, up) + grid[i][j];
            }
        }
        
        return dp[m - 1][n - 1];
    }
}
```
