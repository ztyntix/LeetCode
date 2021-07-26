## Problem

https://leetcode.com/problems/count-and-say/

## Problem Description

```
The count-and-say sequence is a sequence of digit strings defined by the recursive formula:

countAndSay(1) = "1"
countAndSay(n) is the way you would "say" the digit string from countAndSay(n-1), which is then converted into a different digit string.
To determine how you "say" a digit string, split it into the minimal number of groups so that each group is a contiguous section all of the same character. Then for each group, say the number of characters, then say the character. To convert the saying into a digit string, replace the counts with a number and concatenate every saying.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public String countAndSay(int n) {
        if (n == 1) return "1";
        
        String last = "1";
        for (int i = 2; i <= n; i++) {
            last = count(last);
            System.out.println(last);
        }
        
        return last;
    }
    
    private String count(String input) {
        if (input.length() == 0) return "";
        
        char prev = input.charAt(0);
        int count = 0;
        String ans = "";
        for (int i = 0; i < input.length(); i++) {
            if (input.charAt(i) == prev) {
                count++;
            } else {
                ans += String.valueOf(count) + prev;
                prev = input.charAt(i);
                count = 1;
            }
        }
        return ans += String.valueOf(count) + prev;
    }
}
```
