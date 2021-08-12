## Problem

https://leetcode.com/problems/balanced-binary-tree/

## Problem Description

```
Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

a binary tree in which the left and right subtrees of every node differ in height by no more than 1.

 

Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: true
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
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        
        int left = getDepth(root.left);
        int right = getDepth(root.right);
        
        return Math.abs(left - right) <= 1 && isBalanced(root.left) && isBalanced(root.right);
    }
    
    private int getDepth(TreeNode root) {
        if (root == null) return 0;
        
        int left = getDepth(root.left);
        int right = getDepth(root.right);
        
        return Math.max(left, right) + 1;
    }
}
```
