## Problem

https://leetcode.com/problems/sum-root-to-leaf-numbers/

## Problem Description

```
You are given the root of a binary tree containing digits from 0 to 9 only.

Each root-to-leaf path in the tree represents a number.

For example, the root-to-leaf path 1 -> 2 -> 3 represents the number 123.
Return the total sum of all root-to-leaf numbers. Test cases are generated so that the answer will fit in a 32-bit integer.

A leaf node is a node with no children.

 

Example 1:


Input: root = [1,2,3]
Output: 25
Explanation:
The root-to-leaf path 1->2 represents the number 12.
The root-to-leaf path 1->3 represents the number 13.
Therefore, sum = 12 + 13 = 25.
```

## Code

-Support Language: JAVA

```JAVA
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {   
    int ans = 0;
    
    public int sumNumbers(TreeNode root) {
        sum(root, 0);
        return ans;
    }
    
    private void sum(TreeNode root, int num) {
        if (root == null) return;
        
        if (root.left == null && root.right == null) {
            ans += num * 10 + root.val;
        }
        
        sum(root.left, 10 * num + root.val);
        sum(root.right, 10 * num + root.val);
    }
}
```
