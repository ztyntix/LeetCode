## Problem

https://leetcode.com/problems/zigzag-conversion/

## Problem Description

```
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

Example 1:

Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1) return s;
        
        String[] ss = new String[numRows];
        for(int i = 0 ; i < numRows; i++) {
            ss[i] = "";
        }
        
        int index = 0, step = -1;
        for (int i = 0; i < s.length(); i++) {
            ss[index] += s.charAt(i);
            if (i % (numRows - 1) == 0) {
                step *= -1;
            }
            
            index += step;
        }
        
        String ans = "";
        for(int i = 0; i < ss.length; i++) {
            ans += ss[i];
        }
        return ans;
    }
}
```
