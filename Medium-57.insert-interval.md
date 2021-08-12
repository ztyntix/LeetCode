## Problem

https://leetcode.com/problems/insert-interval/

## Problem Description

```
Given a set of non-overlapping intervals, insert a new interval into the intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.

 

Example 1:

Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        if (intervals == null || (intervals.length == 0 && newInterval.length == 0)) return intervals;
        
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        
        int left = newInterval[0], right = newInterval[1];
        List<int[]> ans = new ArrayList<>();
        
        for (int i = 0; i < intervals.length; i++) {
            if (intervals[i][1] < left) {
                ans.add(new int[] {intervals[i][0], intervals[i][1]});
            }else if (intervals[i][0] > right) {
                ans.add(new int[] {left, right});
                left = intervals[i][0];
                right = intervals[i][1];
            } else {
                right = Math.max(right, intervals[i][1]);
                left = Math.min(left, intervals[i][0]);
            }
        }
        
        ans.add(new int[] {left, right});
        return ans.toArray(new int[ans.size()][]);
    }
}
```
