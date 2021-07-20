## Problem

https://leetcode.com/problems/valid-parentheses/

## Problem Description

```
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
 

Example 1:

Input: s = "()"
Output: true
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public boolean isValid(String s) {
        if (s == null || s.length() == 0) return true;
        Stack<Character> ss = new Stack<>();
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(' || c == '{' || c == '[') {
                ss.push(c);
            } else {
                if (ss.size() == 0 || !isValid(c, ss.pop())) return false;
            }
        }
        
        return ss.size() == 0;
    }
    
    private boolean isValid(char right, char left) {
        return left == '{' && right == '}' ||
                left == '[' && right == ']'  ||
                left == '(' && right == ')';
    }
}
```
