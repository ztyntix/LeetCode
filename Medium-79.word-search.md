## Problem

https://leetcode.com/problems/word-search/

## Problem Description

```
Given an m x n grid of characters board and a string word, return true if word exists in the grid.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

 

Example 1:


Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
Output: true

Example 2:


Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
Output: false

```

## Code

-Support Language: JAVA

```JAVA

class Solution {
    public boolean exist(char[][] board, String word) {
        int m = board.length, n = board[0].length;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                boolean[][] used = new boolean[m][n];
                if (search(board, word, i, j, 0, used)) return true;
            }
        }
        
        return false;
    }
    
    private boolean search(char[][] board, String word, int i, int j, int index, boolean[][] used) {
        if (index >= word.length()) return true;
        
        if (i >= board.length || j >= board[0].length || i < 0 || j < 0) return false;
        if (used[i][j] || board[i][j] != word.charAt(index)) return false;
        
        used[i][j] = true;
        
        if (search(board, word, i + 1, j, index + 1, used) ||
            search(board, word, i, j + 1, index + 1, used) ||
            search(board, word, i - 1, j, index + 1, used) ||
            search(board, word, i, j - 1, index + 1, used)) {
            return true;
        }
        
        used[i][j] = false;
        return false;
        
    }
}
```
