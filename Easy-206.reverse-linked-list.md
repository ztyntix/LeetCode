## Problem

https://leetcode.com/problems/reverse-linked-list/

## Problem Description

```

Given the head of a singly linked list, reverse the list, and return the reversed list.

 

Example 1:


Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
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
    public ListNode reverseList(ListNode head) {
        ListNode prev = new ListNode(0);
        ListNode ans = prev;
        
        while (head != null) {
            ListNode newNode =  new ListNode(head.val);
            newNode.next = prev.next;
            prev.next = newNode;
            head = head.next;
        }
        
        return ans.next;
    }
}
```
