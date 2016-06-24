---
layout: post
title: LCA for BST/Binary Tree
---

### Description - BST/BT


### Analysis
1. For BST: use the property of BST
2. For BT: 1 pass search -> recursive solution


### Solution
```python
class Solution(object): # BST
    def lca(self, root, s, b):
        if s.val > root.val:
            return self.lca(root.right, s, b)
            
        if b.val < root.val:
            return self.lca(root.left, s, b)

        return root
    
    def lowestCommonAncestor(self, root, p, q):
        """
        :type root: TreeNode
        :type p: TreeNode
        :type q: TreeNode
        :rtype: TreeNode
        """
        s, b = None, None
        if p.val > q.val:
            s, b = q, p
        else:
            s, b = p, q
        
        return self.lca(root, s, b)
        
        
class Solution(object): # ST
    def lowestCommonAncestor(self, root, p, q):
        """
        :type root: TreeNode
        :type p: TreeNode
        :type q: TreeNode
        :rtype: TreeNode
        """
        if root == None or root == p or root == q:
            return root
        
        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)
        
        if left != None and right != None:
            return root
        if left != None:
            return left
        if right != None:
            return right
        
        return None
```

### Source
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree
