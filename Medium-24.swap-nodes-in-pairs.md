## Problem

https://leetcode.com/problems/swap-nodes-in-pairs/

## Problem Description

```
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

 
Example 1:


Input: head = [1,2,3,4]
Output: [2,1,4,3]
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
    public ListNode swapPairs(ListNode head) {
        ListNode ans = new ListNode(0);
        ListNode cur = ans;
        ans.next = head;
        
        if (head == null) return null;
        ListNode first = head, second = head.next;
        
        while (first != null && second != null) {
            ListNode nextStart = second.next;
            
            cur.next = second;
            cur.next.next = first;
            first.next = nextStart;
            
            first = first.next;
            second = first == null ? null : first.next;
            cur = cur.next.next;
        }
        return ans.next;
    }
}
```
