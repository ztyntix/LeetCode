## Problem

https://leetcode.com/problems/maximum-depth-of-binary-tree/

## Problem Description

```
Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

 

Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: 3
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
    public int maxDepth(TreeNode root) {
        return getDepth(root);
    }
    
    private int getDepth(TreeNode root) {
        if (root == null) return 0;
        
        int left = getDepth(root.left);
        int right = getDepth(root.right);
        return Math.max(left, right) + 1;
    }
}
```
