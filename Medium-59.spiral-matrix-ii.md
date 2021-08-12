## Problem

https://leetcode.com/problems/spiral-matrix-ii/

## Problem Description

```
Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

 
Example 1:


Input: n = 3
Output: [[1,2,3],[8,9,4],[7,6,5]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix = new int[n][n];
        
        int left = 0, right = n - 1, up = 0, down = n - 1;
        int num = 1;
        while (num <= n * n) {
            for (int j = left; j <= right; j++) {
                matrix[up][j] = num++;
            }
            up++;
            
            for (int i = up; i <= down; i++) {
                matrix[i][right] = num++;
            }
            right--;
            
            if (up > down || right < left) break;
            
            for (int j = right; j >= left; j--) {
                matrix[down][j] = num++;
            }
            down--;
            
            for (int i = down; i >= up; i--) {
                matrix[i][left] = num++;
            }
            left++;
        }
        
        return matrix;
    }
}
```
