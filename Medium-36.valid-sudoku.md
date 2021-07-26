## Problem

https://leetcode.com/problems/valid-sudoku/

## Problem Description

```
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] == '.') continue;
                if (!isValid(board, i, j)) return false;
            }
        }
        
        return true;
    }
    
    private boolean isValid(char[][] board, int i, int j) {
        char c = board[i][j];
        for (int m = 0; m < 9; m++) {
            if (m == i) continue;
            if (board[m][j] == board[i][j]) return false;
        }
        
        for (int n = 0; n < 9; n++) {
            if (n == j) continue;
            if (board[i][n] == board[i][j]) return false;
        }
        
        for (int n = 0; n < 9; n++) {
            int ni = (i / 3) * 3 + n / 3;
            int nj = (j / 3) * 3 + n % 3;
            
            if (ni == i && nj == j) continue;
            if (board[ni][nj] == board[i][j]) return false;
        }
        
        return true;
    }
}
```
