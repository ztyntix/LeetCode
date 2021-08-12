## Problem

https://leetcode.com/problems/path-sum-ii/

## Problem Description

```
Given the root of a binary tree and an integer targetSum, return all root-to-leaf paths where each path's sum equals targetSum.

A leaf is a node with no children.

 

Example 1:


Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: [[5,4,11,2],[5,8,4,5]]
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
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        List<List<Integer>> ans = new ArrayList<>();
        
        calculatePath(ans, new ArrayList<>(), targetSum, root);
        return ans;
    }
    
    private void calculatePath(List<List<Integer>> ans, List<Integer> temp, int targetSum, TreeNode root) {
        if (root == null) return;
        
        temp.add(root.val);
        
        if (root.left == null && root.right == null) {
            if (targetSum == root.val) {
                ans.add(new ArrayList<>(temp));
                temp.remove(temp.size() - 1);
                return;
            }
        }
        
        calculatePath(ans, temp, targetSum - root.val, root.left);
        calculatePath(ans, temp, targetSum - root.val, root.right);
        temp.remove(temp.size() - 1);
        
    }
}
```
