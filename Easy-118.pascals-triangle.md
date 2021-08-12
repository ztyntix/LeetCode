## Problem

https://leetcode.com/problems/pascals-triangle/

## Problem Description

```
Given an integer numRows, return the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:


 

Example 1:

Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> lastRow = new ArrayList<>();
        lastRow.add(1);
        ans.add(lastRow);
        
        for (int i = 1; i < numRows; i++) {
            List<Integer> temp = new ArrayList<>();
            for (int j = 0; j <= i; j++) {
                int first = j == 0 ? 0 : ans.get(i - 1).get(j - 1);
                int second = j == i ? 0 : ans.get(i - 1).get(j);
                temp.add(first + second);
            }
            ans.add(new ArrayList<>(temp));
        }
        
        return ans;
    }
}
```
