## Problem

https://leetcode.com/problems/binary-tree-inorder-traversal/

## Problem Description

```

Given the root of a binary tree, return the inorder traversal of its nodes' values.

 

Example 1:


Input: root = [1,null,2,3]
Output: [1,3,2]
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        
        dfs(ans, root);
        return ans;
    }
    
    private void dfs(List<Integer> ans, TreeNode root) {
        if (root == null) return;
        
        dfs(ans, root.left);
        ans.add(root.val);
        dfs(ans, root.right);
    }
}
```
