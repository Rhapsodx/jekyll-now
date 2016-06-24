---
layout: post
title: Reverse Link List
---


### Description
Reverse a singly linked list.

### Analysis
Reverse the node pairs.

### Solution
```python
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        node_pairs = []
        
        if head is None or head.next is None:
            return head
        
        p = head
        pre = None
        while p:
            if pre is not None:
                node_pairs.append((pre, p))
            pre = p
            p = p.next
        
        for pair in reversed(node_pairs):
            pre, p = pair
            p.next = pre
            pre.next = None
            
        return node_pairs[-1][1]
```

### Source
https://leetcode.com/problems/reverse-linked-list/
