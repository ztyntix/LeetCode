## Problem

https://leetcode.com/problems/longest-palindromic-substring/

## Problem Description

```
Given a string s, return the longest palindromic substring in s.


Example 1:

Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.

Example 2:

Input: s = "cbbd"
Output: "bb"
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    class Solution {
    int ans = 0, left = 0, right = 0;
    public String longestPalindrome(String s) {
        if (s == null || s.length() == 0) return null;
        
        for (int i = 0; i < s.length(); i++) {
            expand(s, i, i);
            expand(s, i, i + 1);
        }
        
        return s.substring(left, right + 1);
    }
    
    private void expand(String s, int i, int j) {
        int len = i == j ? -1 : 0;
        while (i >= 0 && j < s.length() && s.charAt(i) == s.charAt(j)) {
            i--;
            j++;
            len += 2;
        }
        if (len > ans) {
            left = i + 1;
            right = j - 1;
            ans = len;
        }
    }
}
```
