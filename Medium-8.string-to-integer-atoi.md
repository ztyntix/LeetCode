## Problem

https://leetcode.com/problems/string-to-integer-atoi/

## Problem Description

```
Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer (similar to C/C++'s atoi function).

The algorithm for myAtoi(string s) is as follows:

Read in and ignore any leading whitespace.
Check if the next character (if not already at the end of the string) is '-' or '+'. Read this character in if it is either. This determines if the final result is negative or positive respectively. Assume the result is positive if neither is present.
Read in next the characters until the next non-digit charcter or the end of the input is reached. The rest of the string is ignored.
Convert these digits into an integer (i.e. "123" -> 123, "0032" -> 32). If no digits were read, then the integer is 0. Change the sign as necessary (from step 2).
If the integer is out of the 32-bit signed integer range [-231, 231 - 1], then clamp the integer so that it remains in the range. Specifically, integers less than -231 should be clamped to -231, and integers greater than 231 - 1 should be clamped to 231 - 1.
Return the integer as the final result.
Note:

Only the space character ' ' is considered a whitespace character.
Do not ignore any characters other than the leading whitespace or the rest of the string after the digits.
 

Example 1:

Input: s = "42"
Output: 42
Explanation: The underlined characters are what is read in, the caret is the current reader position.
Step 1: "42" (no characters read because there is no leading whitespace)
         ^
Step 2: "42" (no characters read because there is neither a '-' nor '+')
         ^
Step 3: "42" ("42" is read in)
           ^
The parsed integer is 42.
Since 42 is in the range [-231, 231 - 1], the final result is 42.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int myAtoi(String s) {
        int ans = 0, flag = 1, i = 0;
        s = s.trim();
        
        if (s == null || s.length() == 0) return 0;
        
        if (s.charAt(0) == '-' || s.charAt(0) == '+') {
            flag = s.charAt(0) == '-' ? -1 : 1;
            i = 1;
        }
        
        for (;i < s.length(); i++) {
            char c = s.charAt(i);
            if (Character.isDigit(c)) {
                int d = c - '0';
                int rightBound = (Integer.MAX_VALUE - d) / 10;
                int leftBound = (Integer.MIN_VALUE - d) / 10;
                if (ans > Integer.MAX_VALUE / 10 || (ans == Integer.MAX_VALUE / 10 && d > 7)) {
                    return flag == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
                }
                ans = ans * 10 + d;
            } else {
                break;
            }
        }
        return ans * flag;
    }
}
```
