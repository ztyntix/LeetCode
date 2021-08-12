## Problem

https://leetcode.com/problems/summary-ranges/

## Problem Description

```
You are given a sorted unique integer array nums.

Return the smallest sorted list of ranges that cover all the numbers in the array exactly. That is, each element of nums is covered by exactly one of the ranges, and there is no integer x such that x is in one of the ranges but not in nums.

Each range [a,b] in the list should be output as:

"a->b" if a != b
"a" if a == b
 

Example 1:

Input: nums = [0,1,2,4,5,7]
Output: ["0->2","4->5","7"]
Explanation: The ranges are:
[0,2] --> "0->2"
[4,5] --> "4->5"
[7,7] --> "7"
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public List<String> summaryRanges(int[] nums) {
        List<String> ans = new ArrayList<>();
        if (nums == null || nums.length < 1) return ans;
        
        int start = nums[0];
        String range = "";
        
        for (int i = 0; i < nums.length; i++) {
            if (i < nums.length - 1 && nums[i + 1] == nums[i] + 1) continue;
            else {
                range = String.valueOf(start);
                if (nums[i] != start) range = range + "->" + nums[i];
                
                ans.add(range);
                start = i < nums.length - 1 ? nums[i + 1] : 0;
            }
        }
        
        return ans;
    }
}
```
