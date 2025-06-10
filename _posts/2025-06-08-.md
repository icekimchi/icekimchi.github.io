---
title: "[LeetCode] Top K Frequent Elements"
date: 2025-6-8 23:00:00 +0900
categories: [Algorithm, Java]
tags: [Java, Algorithm]
---

# 💡 Top K Frequent Elements

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

Example 1:  
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]

Example 2:  
Input: nums = [1], k = 1
Output: [1]

### 💡 PriorityQueue

- Different from the original Queue, Priority Queue outputs data with higher priority first.
- basically, Asending
- Use `Comparator`, `Comparable` if want to change it to descending.

```java
PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

pq.add(5);
pq.add(3);
pq.add(10);

System.out.println(pq.poll()) // 10 print
```

### 💡 Methods of PriorityQueue

| method     | describe                                                                                           |
| ---------- | -------------------------------------------------------------------------------------------------- |
| add()      | Returns true if the insertion is successful; otherwise, throws an `IllegalStateException`          |
| element()  | Retrieves the element without removing it. If the queue is empty, throws a NoSuchElementException. |
| offer(E e) | Stores an object in the Queue. Returns `true` if successful, `false` if not.                       |
| poll()     | Retrieves and removes an object from the queue. Returns `null` if the queue is empty.              |

### 💡 EntrySet()

```java
Set<Map.Entry<String, Integer>> entries = map.entrySet();
```

- If then retrieves that set view of this map using `entrySet()`, allowing further manipulation of iteration.

```java
for (Map.Entry<String, Integer> entry: entries){
    System.out.println(entry.getKey() + "has " + entry.getValue());
}
```

### 💡 Answer

```java
import java.util.*;

class Solution {
    public int[] topKFrequent(int[] nums, int k) {

        //
        Map<Integer, Integer> numMap = new HashMap<>();
        for (int num: nums){
            numMap.put(num, numMap.getOrDefault(num, 0) + 1);
        }

        PriorityQueue<Map.Entry<Integer, Integer>> maxHeap = new PriorityQueue<>((a, b) -> b.getValue() - a.getValue());

    for (Map.Entry<Integer, Integer> entry : numMap.entrySet()) {
        maxHeap.offer(entry);
    }

    int[] result = new int[k];
    for (int i = 0; i < k; i++) {
        result[i] = maxHeap.poll().getKey();
    }

    return result;
    }
}
```

### 💡 Why I use PriorityQueue?

To count the frequency of each number, I used a Map data structure.
However, a HashMap only provides key-value mapping and does not support ordering by value (frequency).

Therefore, I used a PriorityQueue to sort the entries by frequency. Also, if I extract the entries from the HashMap into a list and then sort it(`O(nlogn)`), it requires more time than using a PriorityQueue.
