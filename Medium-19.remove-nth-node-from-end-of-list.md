## Problem

https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## Problem Description

```
Given the head of a linked list, remove the nth node from the end of the list and return its head.

Example 1:


Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

## Code

- Support Language: JAVA

```JAVA
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode cur = head, forward = head;
        for (int i = 0; i < n; i++) {
            forward = forward.next;
        }
        
        ListNode prev = new ListNode(0);
        prev.next = head;
        
        ListNode ans = prev;
        while (forward != null) {
            forward = forward.next;
            cur = cur.next;
            prev = prev.next;
        }
        prev.next = cur.next;
        
        return ans.next;
    }
}
```
