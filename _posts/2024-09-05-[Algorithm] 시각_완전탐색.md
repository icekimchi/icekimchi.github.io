---
title: "[Algorithm] 시각_완전탐색"
date: 2024-9-4 23:00:00 +0900
categories: [Algorithm, Python]
tags: [Python, 알고리즘, 소수 판별]
---

# 💡 시각

정수 N이 입력되면 00시00분00초부터 N시59분59초 까지의 모든 시각 중에서 3이 하나라도 포함되는 모든 경우의 수를 구하라

### 💡 내가 쓴 코드

```python
N = int(input())

clock = [0, 0, 0]
ans = 0

for sec in range((N+1)*60*60-1):
    clock[0] += 1

    if clock[0]//60:
        clock[1] += 1
        clock[0] = 0

    if clock[1]//60:
        clock[2] += 1
        clock[1] = 0

    if "3" in ''.join(str(s) for s in clock):
        ans += 1
print(ans)
```

- 하나의 반복문으로 작성하였고, 시계를 리스트로 표현하였다.
- 코드 안에서 60초일때와 60분일때 실제 시계처럼 동작하도록 리스트 값을 변경해주었다.
- 마지막에 리스트를 문자열로 합쳐 3이 있는지 없는지를 판별하였다.

### 💡 알고리즘 설명

이 문제는 모든 경우를 하나씩 세서 쉽게 풀 수 있는 경우다. 하루는 86400초로, 23이 입력되더라고 모든 경우는 86400가지밖에 존재하지 않기 때문이다.

### 💡 바꾼 코드

```python
N = int(input())
ans = 0

for h in range(N+1):
    for m in range(60):
        for s in range(60):
            if "3" in str(h)+str(m)+str(s):
                ans += 1

print(ans)
```

- 왜 삼중 반복문을 사용할 생각을 하지 못했을까?
- 반복문을 사용해주어 60초마다 분과 시를 바꿔야 할 필요가 없어졌다.
- 이 코드를 기억할것 !
