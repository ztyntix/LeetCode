## Problem

https://leetcode.com/problems/median-of-two-sorted-arrays/

## Problem Description

```
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

 

Example 1:

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int len1 = nums1.length, len2 = nums2.length, len = len1 + len2;
        
        int mid = len % 2 != 0 ? len / 2 + 1 : len / 2;
        int nums = len % 2 != 0 ? 1 : 2;
        
        
        int i = len1 - 1, j = len2 - 1;
        int ans = 0, count = 0;
        
        while (i >= 0 || j >= 0) {
            int cur1 = i >= 0 ? nums1[i] : -1;
            int cur2 = j >= 0 ? nums2[j] : -1;
            int cur = Math.max(cur1, cur2);
            
            count++;
            if (count >= mid && nums-- > 0) {
                ans += cur;
            }
            
            if (cur == cur1) i--;
            else j--;
            
            if (nums == 0) break;
        }
        
        System.out.println(ans);
        return ans / (len % 2 != 0 ? 1.0 : 2.0);
    }
}
```
