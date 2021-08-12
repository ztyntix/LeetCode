## Problem

https://leetcode.com/problems/binary-tree-right-side-view/

## Problem Description

```
Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

 

Example 1:


Input: root = [1,2,3,null,5,null,4]
Output: [1,3,4]
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
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        
        dfs(root, ans, 0);
        return ans;
    }
    
    private void dfs(TreeNode root, List<Integer> ans, int depth) {
        if (root == null) return;
        
        if (depth >= ans.size()) {
            ans.add(depth, root.val);
        } else {
            ans.set(depth, root.val);
        }
        
        dfs(root.left, ans, depth + 1);
        dfs(root.right, ans, depth + 1);
    }
}
```
