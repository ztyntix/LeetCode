## Problem

https://leetcode.com/problems/reverse-words-in-a-string/

## Problem Description

```
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

 

Example 1:

Input: s = "the sky is blue"
Output: "blue is sky the"
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public String reverseWords(String s) {
        if (s == null || s.length() == 0) return s;
        
        String[] ss = s.split(" ");
        String ans = "";
        
        for (String w: ss) {
            if (w.length() == 0) continue;
            ans = w + " " + ans;
        } 
        return ans.length() > 0 ? ans.substring(0, ans.length() - 1) : ans;
    }
}
```
