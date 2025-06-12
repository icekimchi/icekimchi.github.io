---
title: "[LeetCode] Longest Substring Without Repeating Characters"
date: 2025-6-11 23:00:00 +0900
categories: [Algorithm, Java]
tags: [Java, Algorithm]
---

# 💡 Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without duplicate characters.

**Example 1:**
**Input:** s = "abcabcbb"
**Output:** 3
**Explanation:** The answer is "abc", with the length of 3.

**Example 3:**
**Input:** s = "pwwkew"
**Output:** 3
**Explanation:** The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring. // subsequence

### 💡 substring vs subsequence

- suqsequence : a sequence that can be derived from another sequence by deleting some or no elements **without changing the order** of the remaining elements
- substring : **contiguous** sequence of characters within a string

  "pwwkew" -> pwke is subsequence
  "wke" -> substring So, the answer is wke

### 💡 Constraints

- What if the length is 0 -> the empty string.
  0 <= s.length <= 5\*10^4
- What if string has symbols and spaces?
  s consists of English letter, digits, symbols and spaces.

### 💡 How to solve? What data structure.?

- Data structure : Set, ArrayList..

### 💡 First Solution - Just use String and For loop

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {

        String temp = "";
        List<String> sub = new ArrayList<>();

        //do for loop putting character of s
        for (char c: s.toCharArray()){
            //if same character happen, then put in list
            if (temp.indexOf(c) != -1){ //if duplicate
                sub.add(temp);
                temp = "" + c;
            } else{
                temp += c;
            }
        }
        sub.add(temp);

        //return max length of list
        int max = 0;
        for (int i=0; i<sub.size(); i++){
            if (sub.get(i).length() >= max){
                max = sub.get(i).length();
            }
        }
        System.out.println(sub);

        return max;
    }
}
```

Complexity : O(N^2)

### 💡 HashMap + Sliding

```java
class Solution {

    public int lengthOfLongestSubstring(String s) {

    //make Set to store substring
    Set<Character> set = new HashSet<>();
    int left = 0, max = 0; //initiate window, max

    //for loop to make substring
    for(int right = 0; right<s.length(); right++){
        char c = s.charAt(right); //extend window

        //if duplicate? then move window
        while(set.contains(c)){
            set.remove(s.charAt(left));
            left++;
        }

        set.add(c); //put c in hashset
        max = Math.max(max, right - left + 1);
    }

    return max;
    }
}
```

complexity : O(n)
