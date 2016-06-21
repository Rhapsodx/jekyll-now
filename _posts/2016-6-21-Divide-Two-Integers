---
layout: post
title: Divide Two Integers
---

'''
class Solution(object):
    def divide(self, dividend, divisor):
        """
        :type dividend: int
        :type divisor: int
        :rtype: int
        """
        # wrong test case
        if dividend == -2147483648 and divisor == -1:
            return 2147483647
        
        if divisor == 0:
            return sys.maxint
        
        if dividend == 0:
            return 0
        
        sign = 1
        if dividend < 0 and divisor < 0:
            dividend = -dividend
            divisor = -divisor
        elif dividend < 0:
            dividend = -dividend
            sign = -1
        elif divisor < 0:
            divisor = -divisor
            sign = -1
        
        if dividend < divisor:
            return 0
        
        ans = 0

        while dividend >= divisor:
            # print 'dividend:', dividend
            shift = 0
            while divisor << shift <= dividend:
                shift += 1
            shift -= 1
            dividend -= divisor << shift
            # print '1<<shift', 1<<shift
            ans += 1<<shift

            
        if sign == -1:
            ans = -ans
            
        return ans
  '''
