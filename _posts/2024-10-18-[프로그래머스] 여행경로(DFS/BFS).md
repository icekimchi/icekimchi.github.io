---
title: "[프로그래머스] 여행경로(DFS/BFS)"
date: 2024-10-18 23:00:00 +0900
categories: [Algorithm, 코딩테스트]
tags: [Python, 알고리즘, 코딩테스트, 설계]
---

# 여행경로

### 💡 초기 재귀로 구현한 DFS 코드

```python
from collections import deque

def DFS(q, dict, answer):
    if not q:
        return answer

    temp = q.popleft()
    answer.append(temp)

    if temp in dict:
        next_dest = dict[temp].pop(0)
        q.append(next_dest)

        if not dict[temp]:
            del dict[temp]

    return DFS(q, dict, answer)

def solution(tickets):
    q = deque(["ICN"])
    answer = []
    dict = {}

    for start, dest in tickets:
        if start in dict:
            dict[start].append(dest)
        else:
            dict[start] = [dest]

    for start in dict:
        dict[start].sort()

    return DFS(q, dict, answer)
```

![alt text](..\images\2024-10-18\기존코드.png)

### 💡 왜 오류가 떴을까?

- 우선, 코드를 많이 짜보지 않아 위의 코드는 완벽한 DFS가 아닌 DFS + BFS가 섞인 코드이다.. 내 실력이 부족한 탓,, 우선! 고쳐야 할 부분은 아래와 같다.
- 모든 티켓을 다 사용해야 하는데, 일부 케이스에서는 잘못된 경로로 인해 티켓이 남아버릴 수 있다.
- 따라서, `백트래킹` 을 적용하여, 경로를 완벽히 탐색한 경우에만 answer에 경로를 추가해주었다. 따라서, 마지막에 출력할 때는 거꾸로 출력을 해주었다.

### 💡 바뀐 코드

```python
def DFS(temp, dict, answer, ticket_count):
    while dict.get(temp):   #키가 존재할 때까지
        next_dest = dict[temp].pop(0)  #dict에서 뽑아서 사용
        DFS(next_dest, dict, answer, ticket_count) #그 다음 경로로 재귀 사용

    # 이 코드가 실행된다는 것은 while문에서 False가 나왔을 때
    # 즉, 전체 경로를 모두 탐색하면 append 함수가 실행된다.
    answer.append(temp)  # 경로를 끝에서부터 쌓아가야 함 (백트래킹)


def solution(tickets):
    answer = []
    dict = {}

    for start, dest in tickets:
        if start in dict:
            dict[start].append(dest)
        else:
            dict[start] = [dest]

    for start in dict:
        dict[start].sort()

    return DFS("ICN", dict, answer, len(tickets))
```

### 💡 stack 을 사용한 DFS

```python
from collections import defaultdict

def solution(tickets):
    graph = defaultdict(list)

    for start, dest in tickets:
        graph[start].append(dest)

    for start in graph:
        graph[start].sort()

    stack = ["ICN"]
    path = []

    while stack:
        route = stack[-1]

        if not graph[route]:
            path.append(stack.pop())
        else:
            next_route = graph[route].pop(0)
            stack.append(next_route)

    return path[::-1]

```

- 딕셔너리.get() 함수를 사용해서 key가 존재하지 않으면 None을 반환하는 함수를 사용하였다. 키가 없어도 오류가 발생하지 않는다.

### 💡 마무리

- 사실, 완벽히 이 코드를 이해하지 못했다,, 대략 이해하는 정도지만 내가 혼자서 구현하는 데 자신이 없어서 앞으로 더 공부해봐야겠다.
