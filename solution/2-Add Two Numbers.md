### Description:  

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:
```python
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

### Solution: 
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        carry = 0 # additive carry
        dummyHead = ListNode(0) # create a new ListNode
        curr = dummyHead 
        
        while l1 is not None or l2 is not None:
            p = l1.val if l1 is not None else 0
            q = l2.val if l2 is not None else 0
            temp = p + q + carry
            curr.next = ListNode(temp % 10) # must be ListNode
            carry = temp // 10
            if l1 is not None:
                l1 = l1.next
            if l2 is not None:
                l2 = l2.next
            curr = curr.next
        
        if carry == 1:
            curr.next = ListNode(1) # final carry
        return dummyHead.next
```