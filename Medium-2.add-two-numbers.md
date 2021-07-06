## Problem

https://leetcode.com/problems/add-two-numbers/

## Problem Description

```
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.


Example 1:

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

## Code

- Support Language: JAVA

```JAVA
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int flag = 0;
        ListNode ans = new ListNode(0);
        ListNode pre = ans;
        while (l1 != null || l2 != null) {
            int sum = flag;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            pre.next = new ListNode(sum % 10);
            pre = pre.next;
            flag = sum / 10;
        }
        
        if (flag > 0) pre.next = new ListNode(1);
        return ans.next;
    }
}
```
