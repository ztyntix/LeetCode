## Problem

https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/

## Problem Description

```
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

 

Example 1:


Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:
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
    public TreeNode sortedArrayToBST(int[] nums) {
        return constructTree(nums, 0, nums.length - 1);
    }
    
    private TreeNode constructTree(int[] nums, int left, int right) {
        if (left > right) return null;
        
        int mid = (left + right) / 2;
        TreeNode root = new TreeNode(nums[mid]);
        root.left = constructTree(nums, left, mid - 1);
        root.right = constructTree(nums, mid + 1, right);
        
        return root;
    }
}
```
