---
layout: post
title: Ugly Number
---

### Descritpion
Write a program to check whether a given number is an ugly number.  
Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.  
Note that 1 is typically treated as an ugly number.  

### Analysis
Every integer larger than 1 can be written as a product of one or more primes.

### Solution
```python
class Solution(object):
    def isUgly(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num <= 0:
            return False
        
        if num%2 != 0 and num%3 != 0 and num%5 != 0 and num != 1:
            return False
        
        while num%2 == 0:
            num/=2
        while num%3 == 0:
            num/=3
        while num%5 == 0:
            num/=5
        
        if num == 1:
            return True
        else:
            return False
```

### Source
https://leetcode.com/problems/ugly-number/
