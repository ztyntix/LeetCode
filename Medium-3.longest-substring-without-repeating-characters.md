## Problem

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Problem Description

```
Given a string s, find the length of the longest substring without repeating characters.

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int ans = 0;
        
        for (int left = 0, right = 0; right < s.length(); right++) 
        {
            char r = s.charAt(right);
            if (map.containsKey(r)) {
                left = Math.max(map.get(r) + 1, left);
            }
            map.put(r, right);
            ans = Math.max(ans, right - left + 1);
        }
        
        return ans;
    }
}
```
