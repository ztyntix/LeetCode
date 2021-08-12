## Problem

https://leetcode.com/problems/plus-one/

## Problem Description

```
Given a non-empty array of decimal digits representing a non-negative integer, increment one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

 

Example 1:

Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int[] plusOne(int[] digits) {
        if (digits == null || digits.length == 0) return digits;
        
        int factor = 1;
        for (int i = digits.length - 1; i >= 0; i--) {
            int sum = digits[i] + factor;
            digits[i] = sum % 10;
            factor = sum / 10;
        }
        
        if (factor == 1) {
            int[] ans = new int[digits.length + 1];
            ans[0] = 1;
            return ans;
        }
        
        return digits;
    }
}
```
