---
title: "[Algorithm] DFS(깊이 우선 탐색) "
date: 2024-10-8 23:00:00 +0900
categories: [Algorithm, Python]
tags: [Python, 알고리즘, 코딩테스트, 설계]
---

# DFS (깊이 우선 탐색)

### 💡 DFS란

- 깊이를 우선해 그래프를 탐색하는 방법이다.
- 노드와 연결된 다른 노드로 이동하고, 또 이동된 노드로 이동하는 방법
- **스택**이나 **재귀함수**를 통해 구현이 가능하다.

특징

- BFS에 비해 메모리 사용률이 적다.
- 찾고자하는 답이 트리에서 멀어질 수록 DFS가 유리
- DFS의 대표적인 순회 방식은 전위 순회(Pro-Order)이다.

### 💡 스택을 구현한 DFS

```python
def DFS(grapth, root):
    visited = [] #방문한 노드를 기록
    stack = [root]

    while(stack): #스택에 남은 것이 없을 때까지
        node = stack.pop() #node : 현재 방문한 노드
        if node not in visited:
            visited.append(node)
            stack.extend(graph[node])
    return visited
```

### 💡 재귀로 구현한 DFS

```python
def DFS(graph, v, visited):
    #현재 노드를 방문 처리
    visited[v] = True
    print(v, end = ' ')

    #현재 노드와 연결된 다른 노드를 재귀적으로 방문
    for i in graph[v]:
        if not visited[i]:
            DFS(graph, i, visited)
```

### 💡 마무리

- 자료구조 시간에 배웠었지만 실제 코드에서 오랫동안 사용을 안 했더니 다 까먹었다..
- DFS를 많이 사용해보는 것만이 살 길이다!
