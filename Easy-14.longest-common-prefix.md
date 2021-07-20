## Problem

https://leetcode.com/problems/longest-common-prefix/

## Problem Description

```
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return null;
        String ans = "";
        
        for (int j = 0; j < strs[0].length(); j++) {
            for (int i = 0; i < strs.length; i++) {
                if (j >= strs[i].length() || strs[i].charAt(j) != strs[0].charAt(j)) return ans;
            }
            ans += strs[0].charAt(j);
        }
        return ans;
    }
}
```
