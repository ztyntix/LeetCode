## Problem

https://leetcode.com/problems/add-binary/

## Problem Description

```
Given two binary strings a and b, return their sum as a binary string.
 

Example 1:

Input: a = "11", b = "1"
Output: "100"
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public String addBinary(String a, String b) {
        String ans = "";
        int add = 0;
        for (int i = a.length() - 1, j = b.length() -1; i >= 0 || j >= 0;) {
            int numA = i >= 0 ? a.charAt(i) - '0' : 0;
            int numB = j >= 0 ? b.charAt(j) - '0' : 0;
            int sum = numA + numB + add;
            
            ans = String.valueOf(sum % 2) + ans;
            add = sum / 2;
            
            if (i >= 0) i--;
            if (j >= 0) j--;
        }
        
        return add == 1 ? "1" + ans : ans;
    }
}
```
