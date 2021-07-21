## Problem

https://leetcode.com/problems/buddy-strings/

## Problem Description

```
Given two strings s and goal, return true if you can swap two letters in s so the result is equal to goal, otherwise, return false.

Swapping letters is defined as taking two indices i and j (0-indexed) such that i != j and swapping the characters at s[i] and s[j].

For example, swapping at indices 0 and 2 in "abcd" results in "cbad".
 

Example 1:

Input: s = "ab", goal = "ba"
Output: true
Explanation: You can swap s[0] = 'a' and s[1] = 'b' to get "ba", which is equal to goal.

Example 2:

Input: s = "aa", goal = "aa"
Output: true
Explanation: You can swap s[0] = 'a' and s[1] = 'a' to get "aa", which is equal to goal.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public boolean buddyStrings(String s, String goal) {
        if (s == null || goal == null || s.length() != goal.length()) return false;
        List<Integer> set = new LinkedList<>();
        HashMap<Character, Integer> map = new HashMap<>();
        
        for (int i = 0; i < goal.length(); i++) {
            map.put(s.charAt(i), map.getOrDefault(s.charAt(i), 0) + 1);
            if (s.charAt(i) == goal.charAt(i)) continue;
            set.add(i);
        }

        if (set.size() == 2) {
            int left = set.get(0);
            int right = set.get(1);
            return s.charAt(left) == goal.charAt(right) && s.charAt(right) == goal.charAt(left);
        }
        
        if (set.size() == 0) {
            for (char c: map.keySet()) {
                if (map.get(c) >= 2) return true;
            }
        }
        return false;
    }
}
```
