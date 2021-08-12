## Problem

https://leetcode.com/problems/rotate-list/

## Problem Description

```
Given the head of a linked list, rotate the list to the right by k places.

 

Example 1:


Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null) return head;
        
        int len = 1;
        ListNode cur = head;
        
        while (cur.next != null) {
            len++;
            cur = cur.next;
        }
        
        k = k % len;
        cur.next = head;
        
        int prevLen = len - k;
        while(prevLen-- > 0) {
            cur = cur.next;
        }
        
        ListNode ans = cur.next;
        cur.next = null;
        
        return ans;
    }
}
```
