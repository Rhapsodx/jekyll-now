---
layout: post
title: Word Break I & II
---

### Description - I
Given a string s and a dictionary of words dict, determine if s can be segmented into a space-separated sequence of one or more dictionary words.

For example, given
s = "leetcode",
dict = ["leet", "code"].

Return true because "leetcode" can be segmented as "leet code".

### Analysis
dp[i] = dp[0:x] && dp[x:i]

### Solution

```python
class Solution(object):

    def wordBreak(self, s, wordDict):
            """
            :type s: str
            :type wordDict: Set[str]
            :rtype: bool
            """
            dp = dict()
            dp[0] = True
            
            for i in range(len(s)):
                if not dp.has_key(i):
                    continue
            
                for word in wordDict:
                    length = len(word)
                    end = i + length
                    if end <= len(s) and s[i:end] == word:
                        dp[end] = True
            
            if dp.has_key(len(s)):
                return True
            else:
                return False
                
class Solution(object):

    mem = dict()

    def match(self, s, wordDict):
        
        # print "search:", s

        if self.mem.has_key(s):
            return self.mem[s]

        ans = False

        for word in wordDict:
            if s[0:len(word)] == word:
                if s[len(word):] == '':
                    return True
                res = self.match(s[len(word):], wordDict)
                if res:
                    return True

        self.mem[s] = ans
        return ans        

    def wordBreak(self, s, wordDict):
            """
            :type s: str
            :type wordDict: Set[str]
            :rtype: bool
            """
            self.mem = dict()
            # wordDict = sorted(wordDict, reverse = True)
            return self.match(s, wordDict)
```



### Description - II
Given a string s and a dictionary of words dict, add spaces in s to construct a sentence where each word is a valid dictionary word.

Return all such possible sentences.

For example, given
s = "catsanddog",
dict = ["cat", "cats", "and", "sand", "dog"].

A solution is ["cats and dog", "cat sand dog"].

### Analysis
Memoization + backtrace

### Solution
```python
class Solution(object):

    mem = dict()

    def search(self, s, wordDict):

        if self.mem.has_key(s):
            return self.mem[s]

        ans = []

        for word in wordDict:
            length = len(word)
            if s[0:length] == word:
                if s[length:] == '':
                    ans.append(word)
                else:
                    rests = self.search(s[length:], wordDict)
                    for rest in rests:
                        ans.append(word + ' ' + rest)

        self.mem[s] = ans
        return ans

    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: Set[str]
        :rtype: List[str]
        """
        self.mem = dict()
        return self.search(s, wordDict)
```
