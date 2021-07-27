## Problem

https://leetcode.com/problems/group-anagrams/

## Problem Description

```
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

 
Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();
        
        for (String s: strs) {
            char[] ca = s.toCharArray();
            Arrays.sort(ca);
            String keyStr = String.valueOf(ca);
            if (!map.containsKey(keyStr)) {
                map.put(keyStr, new ArrayList<>());
            }
            map.get(keyStr).add(s);
        }
        
        return new ArrayList<>(map.values());
    }
}
```
