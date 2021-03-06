## Problem

https://leetcode.com/problems/unique-paths/

## Problem Description

```
A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

 

Example 1:


Input: m = 3, n = 7
Output: 28
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        dp[0][0] = 1;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0 && j == 0) continue;
                int left = j > 0 ? dp[i][j - 1] : 0;
                int up = i > 0 ? dp[i - 1][j] : 0;
                dp[i][j] = left + up;
            }
        }
        return dp[m - 1][n - 1];
    }
}
```
