---
layout: post
title: Rotate List
---

### Description
Given a list, rotate the list to the right by k places, where k is non-negative.

For example:
Given 1->2->3->4->5->NULL and k = 2,
return 4->5->1->2->3->NULL.

### Analysis
1. Find the new start node and end node;
2. Link the old tail to the old head; point the new end node .next to None
Should consider corner cases, e.g., empty list, k == 0.

### Solution
```python

class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        
        # test length
        length = 0
        p = head
        while p:
            length += 1
            p = p.next
            
        if length == 0:
            return head
            
        start = length - (k % length)
        if start == length:
            return head
        
        pre_head = head
        p = head
        ith = 0
        pre_node = None
        while ith < start:
            ith += 1
            pre_node = p
            p = p.next
        new_head = p
        pre_node.next = None
        
        while p.next != None:
            p = p.next
        p.next = pre_head
        
        return new_head
```


### Source
https://leetcode.com/problems/rotate-list/
