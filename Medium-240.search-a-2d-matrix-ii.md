## Problem

https://leetcode.com/problems/search-a-2d-matrix-ii/

## Problem Description

```
Write an efficient algorithm that searches for a target value in an m x n integer matrix. The matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
 

Example 1:


Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5
Output: true
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length, n = matrix[0].length;
        
        for (int i = m - 1, j = 0; i >= 0 && j < n; ) {
            if (matrix[i][j] == target) return true;
            else if (matrix[i][j] < target) j++;
            else i--;
        }
        
        return false;
    }
}
```
