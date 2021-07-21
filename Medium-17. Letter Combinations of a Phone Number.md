## Problem

https://leetcode.com/problems/letter-combinations-of-a-phone-number/

## Problem Description

```
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.


Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    List<String> ans = new ArrayList<>();
    
    public List<String> letterCombinations(String digits) {
        if (digits == null || digits.length() == 0) return new ArrayList<>();
        String[] map = new String[] {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
        
        dfs(map, digits, 0, "");
        return ans;
        
    }
    
    private void dfs(String[] map, String digits, int index, String res) {
        if (index >= digits.length()) {
            ans.add(res);
            return;
        }
        
        String options = map[digits.charAt(index) - '0'];
        for (int j = 0; j < options.length(); j++) {
            dfs(map, digits, index + 1, res + options.charAt(j));
        }
    }
}
```
