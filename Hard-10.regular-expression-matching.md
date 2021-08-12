## Problem

https://leetcode.com/problems/regular-expression-matching/

## Problem Description

```
Given an input string s and a pattern p, implement regular expression matching with support for '.' and '*' where:

'.' Matches any single character.​​​​
'*' Matches zero or more of the preceding element.
The matching should cover the entire input string (not partial).

 

Example 1:

Input: s = "aa", p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
Example 2:

Input: s = "aa", p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

## Code

-Support Language: JAVA

```JAVA
/*
dp[i][j] represent: strting s with length i matches string p with length j;
1. If s.charAt(i) == p.charAt(j) dp[i][j] = dp[i - 1][j - 1];
2. If p.charAt(j) == '.' dp[i][j] = dp[i - 1][j - 1];
3. If p.charAt(j) == '*', it should have 2 sub conditions:
    1. s.charAt(i) != p.charAt(j - 1): dp[i][j - 2];
    2. s.charAt(i) == p.charAt(j - 1) || p.charAt(j) == '.'
        a* == ""      dp[i][j] = dp[i][j - 2];
        a* == "a"     dp[i][j] = dp[i][j - 1];
        a* == "a...a" dp[i][j] = dp[i - 1][j];
*/
class Solution {
    public boolean isMatch(String s, String p) {
        int sLen = s.length(), pLen = p.length();
        
        boolean[][] dp = new boolean[sLen + 1][pLen + 1];
        dp[0][0] = true;
        
        for (int j = 1; j <= pLen; j++) {
            dp[0][j] = p.charAt(j - 1) == '*' && dp[0][j - 2];
        }
        
        for (int i = 1; i <= sLen; i++) {
            for (int j = 1; j <= pLen; j++) {
                // case 1 and 2
                if (s.charAt(i - 1) == p.charAt(j - 1) || p.charAt(j - 1) == '.') {
                    dp[i][j] = dp[i - 1][j - 1];
                }
                else if (p.charAt(j - 1) == '*')
                {
                    if (s.charAt(i - 1) == p.charAt(j - 2) || p.charAt(j - 2) == '.') 
                        dp[i][j] = dp[i - 1][j] || dp[i][j - 1] || dp[i][j - 2];
                    else dp[i][j] = dp[i][j - 2];
                }
            }
        }
        
        return dp[sLen][pLen];
    }
}
```
