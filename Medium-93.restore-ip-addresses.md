## Problem

https://leetcode.com/problems/restore-ip-addresses/

## Problem Description

```
Given a string s containing only digits, return all possible valid IP addresses that can be obtained from s. You can return them in any order.

A valid IP address consists of exactly four integers, each integer is between 0 and 255, separated by single dots and cannot have leading zeros. For example, "0.1.2.201" and "192.168.1.1" are valid IP addresses and "0.011.255.245", "192.168.1.312" and "192.168@1.1" are invalid IP addresses. 

 

Example 1:

Input: s = "25525511135"
Output: ["255.255.11.135","255.255.111.35"]
```

## Code

-Support Language: JAVA

```JAVA
class Solution {
    public List<String> restoreIpAddresses(String s) {
        List<String> ans = new ArrayList<>();
        if (s == null || s.length() < 4 || s.length() > 12) return ans;
        
        dfs(s, "", ans, 0, 0);
        return ans;
    }
    
    private void dfs(String s, String temp, List<String> ans, int index, int count) {
        if (index >= s.length()) {
            if (count == 4) {
                ans.add(temp.substring(0, temp.length() - 1));    
            }
            
            return;
        }
        
        if (s.charAt(index) == '0') {
            temp += "0" + ".";
            dfs(s, temp, ans, index + 1, count + 1);
            return;
        }
        
        for (int len = 1; len <= 3; len++) {
            int right = index + len;
            if (right > s.length()) break;
            String next = s.substring(index, right);
            int nextValue = Integer.valueOf(next);
            if (nextValue > 0 && nextValue <= 255) {
                dfs(s, temp + next + ".", ans, index + len, count + 1);
            }
        }
    }
}
```
