## Problem

https://leetcode.com/problems/merge-two-sorted-lists/

## Problem Description

```
Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.


Example 1:

Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
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
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode cur = new ListNode(0);
        ListNode ans = cur;
        while (l1 != null || l2 != null) {
            int val1 = l1 == null ? Integer.MAX_VALUE : l1.val;
            int val2 = l2 == null ? Integer.MAX_VALUE : l2.val;
            int min = Math.min(val1, val2);
            
            cur.next = new ListNode(min);
            cur = cur.next;
            
            if (min == val1) l1 = l1.next;
            else l2 = l2.next;
        }
        
        return ans.next;
    }
}
```
