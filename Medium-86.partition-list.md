## Problem

https://leetcode.com/problems/partition-list/

## Problem Description

```

Given the head of a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

 

Example 1:


Input: head = [1,4,3,2,5,2], x = 3
Output: [1,2,2,4,3,5]
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
    public ListNode partition(ListNode head, int x) {
        ListNode small = new ListNode(0);
        ListNode large = new ListNode(0);
        ListNode largeCur = large, smallCur = small;
        
        while (head != null) {
            if (head.val >= x) {
                largeCur.next = new ListNode(head.val);
                largeCur = largeCur.next;
            } else {
                smallCur.next = new ListNode(head.val);
                smallCur = smallCur.next;
            }
            
            head = head.next;
        }
        
        smallCur.next = large.next;
        return small.next;
    }
}
```
