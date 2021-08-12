## Problem

https://leetcode.com/problems/merge-sorted-array/

## Problem Description

```

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

 

Example 1:

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index = m + n - 1, i = m - 1, j = n - 1; 
        
        while (i >= 0 && j >= 0) {
            int val = Math.max(nums1[i], nums2[j]);
            nums1[index--] = val;
            if (nums1[i] == val) i--;
            else j--;
        }
        
        while (i >= 0) {
            nums1[index--] = nums1[i--];
        }
        
        while (j >= 0) {
            nums1[index--] = nums2[j--];
        }
    }
}
```
