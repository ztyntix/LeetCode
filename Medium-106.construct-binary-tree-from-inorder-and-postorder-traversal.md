## Problem

https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/

## Problem Description

```
Given two integer arrays inorder and postorder where inorder is the inorder traversal of a binary tree and postorder is the postorder traversal of the same tree, construct and return the binary tree.

 

Example 1:


Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
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
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        return constructTree(inorder, 0, inorder.length - 1, postorder, postorder.length - 1);
    }
    
    private TreeNode constructTree(int[] inorder, int left, int right, int[] postorder, int index) {
        if (left > right || index < 0) return null;
            
        int rootIndex = -1;
        for (int i = left; i <= right; i++) {
            if (inorder[i] == postorder[index]) {
                rootIndex = i;
                break;
            }
        }
        
        TreeNode root = new TreeNode(postorder[index]);
        root.left = constructTree(inorder, left, rootIndex - 1, postorder, index - right + rootIndex - 1);
        root.right = constructTree(inorder, rootIndex + 1, right, postorder, index - 1);
        
        return root;
    }
}
```
