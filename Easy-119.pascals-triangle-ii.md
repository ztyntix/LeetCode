## Problem

https://leetcode.com/problems/pascals-triangle-ii/

## Problem Description

```

Given an integer rowIndex, return the rowIndexth (0-indexed) row of the Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:


 

Example 1:

Input: rowIndex = 3
Output: [1,3,3,1]
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> lastRow = new ArrayList<>();
        lastRow.add(1);
        
        for (int i = 1; i <= rowIndex; i++) {
            List<Integer> temp = new ArrayList<>();
            for (int j = 0; j <= lastRow.size(); j++) {
                int first = j == 0 ? 0 : lastRow.get(j - 1);
                int second = j == i ? 0 : lastRow.get(j);
                temp.add(first + second);
            }
            lastRow = temp;
        }
        
        return lastRow;
    }
}
```
