## Problem

https://leetcode.com/problems/remove-element/

## Problem Description

```
Given a string s consists of some words separated by spaces, return the length of the last word in the string. If the last word does not exist, return 0.

A word is a maximal substring consisting of non-space characters only.

 

Example 1:

Input: s = "Hello World"
Output: 5
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int lengthOfLastWord(String s) {
        if (s == null || s.length() == 0) return 0;
        
        String[] words = s.split(" ");
        return words.length == 0 ? 0 : words[words.length - 1].length();
    }
}
```
