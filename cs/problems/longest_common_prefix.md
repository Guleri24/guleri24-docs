---
layout: default
title: Longest Common Prefix
parent: Algorithms
grand_parent: Computer Science
permalink: /cs/algorithms/longest_common_prefix/
---
Date: 28 Aug 2022

# Longest Common Prefix

Write a function to find the longest common prefix string amongest an array of strings.
If there is no common prefix, return an empty string "".

    Example:
        Input: strs = ["flower","flow","flight"]
        Output: "fl"

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        String minLenStr = strs[0];
        for (String s : strs) {
            minLenStr = (s.length() < minLenStr.length()) ? s : minLenStr;
        }
        
        StringBuilder result = new StringBuilder();
        int minLen = minLenStr.length();
        for (int i = 0; i < minLen; i++) {
            boolean check = true;
            for (int j = 1; j < strs.length; j++) {
                if (strs[j].charAt(i) != strs[0].charAt(i)) check = false;
            }
            if (check == true) result.append(strs[0].charAt(i));
            else break;
        }
        return result.toString().isEmpty() ? "" : result.toString();  
    }
}
```

