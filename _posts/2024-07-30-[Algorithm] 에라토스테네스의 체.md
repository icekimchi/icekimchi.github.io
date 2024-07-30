---
title: "[Algorithm] 에라토스테네스의 체 "
date: 2024-7-27 23:00:00 +0900
categories: [Algorithm, Python]
tags: [Python, 알고리즘, 소수 판별]
---

# 💡 에라토스테네스의 체

N보다 작은 모든 소수 판별

### 💡 소수를 구하는 부분

```python
import math

def is_prime_number(x):
    for i in range(2, int(math.sqrt(x))+1):
        if x % i==0:
            return False
    return True

#사용 예시
print(is_prime_number(7))
print(is_prime_number(4))
```

- 이 부분을 지난 post에서 소수를 구하는 알고리즘의 개선 코드라고 하였었다.
- 그러나, 이번 에라토스테네스의 체에서는 이 알고리즘을 N번 반복하여 N보다 작은 모든 소수를 찾는 것이 아니다.

### 💡 알고리즘 설명

1. 2부터 N까지 모든 자연수를 나열한다.
2. 남은 수 중에서 아직 처리하지 않은 가장 작은 소수 i를 찾는다.
3. N보다 작은 i의 배수를 모두 제거한다. 이때, i는 소수이므로 i를 제외하고 제거한다.
4. 더 이상 반복할 수 없을 떄까지 2번과 3번의 과정을 반복한다.

### 💡 코드

```python
import math

n = 10000 #2부터 1000까지의 숫자
array = [True for _ in range(n+1)] #모든 수를 소수로 초기화

for i in range(2, int(math.sqrt(n)) + 1):
    if array[i]==True:
        j = 2
        while i*j<=n:
            array[i*j] = False
            j += 1


#소수 출력
for i in range(2, n+1):
    if array[i]:
        print(i, end=" ")
```

n=6일 때,  
| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| --- | --- | ---| ----| --- | --- | --- |
| True | True | True | True | True | True | True |

i=2라면 4 제거
| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| True | True | True | True | False | True | True |

i=3이라면 6 제거
| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| True | True | True | True | False | True | False |

n=2부터 6까지 2,3,5 남음.
