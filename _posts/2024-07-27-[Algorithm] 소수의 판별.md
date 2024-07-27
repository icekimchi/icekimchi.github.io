---
title: "[JAVA] Scanner 입력 알아보기"
date: 2024-7-27 23:00:00 +0900
categories: [Algorithm, Python]
tags: [Python, 알고리즘, 소수 판별]
---

# 소수의 판별(Prime Number)

소수란 2보다 큰 자연수 중에서 1과 자신을 제외한 자연수로는 나누어 떨어지지 않는 자연수이다.

### 소수 판별 함수

```python
def is_prime_number(x):
    for i in range(2, x):
        if x%i==0:
            return False
    return True

#사용 예시
print(is_prime_number(7))
```

- 시간 복잡도를 계산해보면 O(X) 인 것을 알 수 있다.
- 이는 X가 1000000이라면 2부터 999999까지의 숫자를 모두 계산해봐야 하므로 비효율적이다.

### 알고리즘 개선

- 자연수의 약수의 특징을 생각해보면, 가운데 약수를 기준으로 하여 대칭적으로 2개씩 앞뒤로 묶이는 것을 알 수 있다.
- 가운데 약수를 기준으로 왼쪽에 하나의 약수가 발견된다면 대칭적으로 오른쪽에도 하나의 약수가 있는 것이다.
- 따라서!! 우리는 자연수의 가운데 약수까지만 나누어 떨어지는지 확인하면 된다.

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

- 개선된 소수 판별 알고리즘의 시간 복잡도는 X의 제곱근까지만 계산하면 되므로 O(X\*\*1/2)가 된다.
