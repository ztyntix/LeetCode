## Problem

https://leetcode.com/problems/rotate-image/

## Problem Description

```
You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.


Example 1:


Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public void rotate(int[][] matrix) {
        if (matrix == null || matrix.length == 0) return;
        
        int len = matrix[0].length;
        int up = 0, down = len - 1;
        while (up < down) {
            for (int j = 0; j < matrix[0].length; j++) {
                swap(matrix, up, j, down, j);
            }
            up++;
            down--;
        }
        
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < i; j++) {
                swap(matrix, i, j, j, i);
            }
        }
    }
    
    private void swap(int[][] matrix, int i, int j, int ni, int nj) {
        int temp = matrix[i][j];
        matrix[i][j] = matrix[ni][nj];
        matrix[ni][nj] = temp;
    }
}
```
