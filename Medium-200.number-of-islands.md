## Problem

https://leetcode.com/problems/number-of-islands/

## Problem Description

```
Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

 

Example 1:

Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    int ans = 0;
    
    public int numIslands(char[][] grid) {
        int m = grid.length, n = grid[0].length;
        boolean[][] counted = new boolean[m][n];
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (grid[i][j] == '1' && !counted[i][j]) {
                    ans++;
                    markIsland(grid, i, j, counted);
                }
            }
        }
        return ans;
    }
    
    private void markIsland(char[][] grid, int i, int j, boolean[][] counted) {
        if (i < 0 || j < 0 || i >= grid.length || j >= grid[0].length || grid[i][j] != '1' || counted[i][j]) return;
        
        counted[i][j] = true;
        
        for (int c = 0; c < 4; c++) {
            markIsland(grid, i + 1, j, counted);
            markIsland(grid, i, j + 1, counted);
            markIsland(grid, i - 1, j, counted);
            markIsland(grid, i, j - 1, counted);
        }
    }
}
```
