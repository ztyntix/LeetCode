## Problem

https://leetcode.com/problems/merge-intervals/

## Problem Description

```
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

 

Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```

## Code

-Support Language: JAVA

```JAVA

class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals == null || intervals.length < 2) return intervals;
        
        Arrays.sort(intervals, (a, b) -> (a[0] - b[0]));
        int left = intervals[0][0], right = intervals[0][1];
        List<int[]> ans = new ArrayList<>();
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] > right) {
                ans.add(new int[] {left, right});
                left = intervals[i][0];
                right = intervals[i][1];
            } else {
                right = Math.max(right, intervals[i][1]);
            }
        }
        ans.add(new int[] {left, right});
        
        return ans.toArray(new int[ans.size()][]);
    }
}
```
