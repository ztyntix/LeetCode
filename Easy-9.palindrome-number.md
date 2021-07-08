## Problem

https://leetcode.com/problems/palindrome-number/

## Problem Description

```
Given an integer x, return true if x is palindrome integer.

An integer is a palindrome when it reads the same backward as forward. For example, 121 is palindrome while 123 is not.


Example 1:

Input: x = 121
Output: true
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x != 0 && x % 10 == 0)) {
            return false;
        }

        int revertNum = 0;
        while (x > revertNum) {
            revertNum = revertNum * 10 + x % 10;
            x /= 10;
        }
        return revertNum == x || x == revertNum / 10;
    }
}
```
