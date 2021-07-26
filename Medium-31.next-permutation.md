## Problem

https://leetcode.com/problems/next-permutation/

## Problem Description

```
lexicographically next greater permutation of numbers.

If such an arrangement is not possible, it must rearrange it as the lowest possible order (i.e., sorted in ascending order).

The replacement must be in place and use only constant extra memory.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public void nextPermutation(int[] nums) {
        int a = -1, b = 0;
        
        for (int i = nums.length - 2; i >= 0; i--) {
            if (nums[i] < nums[i + 1]) {
                a = i;
                break;
            }
        }
        
        if (a == -1) {
            Arrays.sort(nums);
            return;
        }
        
        for (int i = nums.length - 1; i >= 0; i--) {
            if (nums[i] > nums[a]) {
                b = i;
                break;
            }
        }
        swap(nums, a, b);
        Arrays.sort(nums, a + 1, nums.length);
    }
    
    private void swap(int[] nums, int a, int b) {
        int temp = nums[a];
        nums[a] = nums[b];
        nums[b] = temp;
    }
}
```
