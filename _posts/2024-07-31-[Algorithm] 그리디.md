---
title: "[Algorithm] 그리디"
date: 2024-7-31 23:00:00 +0900
categories: [Algorithm, Python]
tags: [Python, 알고리즘, 그리디]
---

# 그리디
기준에 따라 좋은 것을 선택하는 알고리즘이므로 문제에서 **가장 큰 순서대로'**, **가장 작은 순서대로**와 같은 기준을 제시해준다면, 대체로 그리디 알고리즘ㅇㄹ 사용했을 때 만족시킬 수 있다.

### 👉 예시 문제
- 가장 큰 화폐 단위부터 돈을 거슬러 주는 문제
```python
n =1260
count = 0

#큰 단위의 화폐부터 차례대로 확인
list = [500, 100, 50, 10]

for coin in list:
    count += n // coin
    n %= coin

#결과 확인
print(coin)
```

### 정당성 확인
- 예를 들어 800원에서 500원 1개, 100원 3개가 아닌 400원 2개가 더 최적의 해이다.
- 위의 예시와 같이 그리디는 최소한의 아이디어를 떠올리고 이것이 정당한지 검토할 수 있어야 답을 도출할 수 있다.

### 💡 큰 수의 법칙
기출 - 2019 국가 교육기곤 코딩 테스트
- 첫째 줄에 N(2<=N<=1000), M(1<=N<=10000), K(1<=k=<=10000) 
- 둘째 줄에 N개의 자연수가 주어진다.
- 입력으로 주는 K는 항상 M보다 작거나 같다.
- 주어진 수들을 M번 더해서 가장 큰 수를 만들어라

```python
N, M, K = map(int, input().split())

data = list(map(int, input().split()))

data.sort() #수 정렬
first = data[N-1]
second = data[N-2]

count = (M // (K+1)) * K
count += M % (K+1)

result += first * count
result += second * (M-count)

#결과 확인
print(result)
```

### 💡 숫자 카드 게임
```python
N, M = map(int, input().split())
data = []
result = 100

for i in range(N):
    tmp = list(map(int, input().split()))
    
    result = max(result, min(tmp))

#결과 출력
print(tmp)
```

