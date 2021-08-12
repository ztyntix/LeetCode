## Problem

https://leetcode.com/problems/remove-duplicates-from-sorted-list/

## Problem Description

```

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

 

Example 1:


Input: head = [1,1,2]
Output: [1,2]
```

## Code

-Support Language: JAVA

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
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) return head;
        
        ListNode cur = head, prev = head;
        ListNode ans = head;
        
        while (cur != null) {
            if (cur.val != prev.val) {
                prev.next = cur;
                prev = prev.next;
            }
            cur = cur.next;
        }
        
        prev.next = cur;
        return ans;
    }
}
```
