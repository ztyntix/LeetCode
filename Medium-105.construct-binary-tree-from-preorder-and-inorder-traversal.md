## Problem

https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/

## Problem Description

```
Given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the binary tree.

 

Example 1:


Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
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
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        return constructTree(inorder, 0, inorder.length - 1, preorder, 0);
    }
    
    private TreeNode constructTree(int[] inorder, int left, int right, int[] preorder, int index) {
        if (left > right || index >= preorder.length) return null;
            
        int rootIndex = -1;
        for (int i = left; i <= right; i++) {
            if (inorder[i] == preorder[index]) {
                rootIndex = i;
                break;
            }
        }
        
        TreeNode root = new TreeNode(preorder[index]);
        root.left = constructTree(inorder, left, rootIndex - 1, preorder, index + 1);
        root.right = constructTree(inorder, rootIndex + 1, right, preorder, index + rootIndex - left + 1);
        
        return root;
    }
}
```
