## Problem

https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/

## Problem Description

```

Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.

 

Example 1:


Input: head = [1,2,3,3,4,4,5]
Output: [1,2,5]

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
        if (head == null || head.next == null) return head;
        
        ListNode cur = head, prev = new ListNode(0), ans = prev;
        
        while (cur != null) {
            int count = 1;
            while (cur.next != null && cur.next.val == cur.val) {
                cur = cur.next;
                count++;
            }
            if (count == 1) {
                prev.next = cur;
                prev = prev.next;
            } else {
                prev.next = cur.next;
            }
            
            cur = cur.next;
        }
        
        return ans.next;
    }
}
```
