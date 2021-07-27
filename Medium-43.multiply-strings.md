## Problem

https://leetcode.com/problems/powx-n/

## Problem Description

```
Implement pow(x, n), which calculates x raised to the power n (i.e., xn).

 
Example 1:

Input: x = 2.00000, n = 10
Output: 1024.00000
```

## Code

- Support Language: JAVA

```JAVAclass Solution {
    public double myPow(double x, int n) {
        if (n == 0) return 1;
        
        if (n < 0) {
            // to avoid integer overflow
            return 1/x * myPow(1/x, -n - 1);
        }
        
        return n % 2 == 0 ? myPow(x * x, n / 2) : myPow(x * x, n / 2) * x;
    }
}
```
