---
title: "[Python] sys.stdin.readline() - 빠른 입력 받기"
date: 2024-02-07 09:54:00 +0900
categories: [Algorithm, Python]
tags: [python, 코딩테스트]
---

# sys.stdin.readline() 입력받기
나는 대부분의 코딩테스트 입력을 `input()` 으로 받았다.  
그런데, `input()` 으로 입력 받아 문제를 풀면 시간 초과 에러가 떠 해결책을 찾으니 `sys.stdin.input()` 을 사용해야 한다고 했다.  

---

### 👉 왜 input()은 느린가?

```python
a = input("출력할 문장")
```

- input() 함수는 출력할 문장을 출력한다.
- 입력 받은 값의 개행문자`(\n)`를 삭제하고 반환한다.
     

### 👉 sys.stdin.readline()
```python
import sys

a = sys.stdin.readline()
```
- 문자열로 입력 받는다.
- 개행 문자를 같이 입력 받는다.
  -> 출력하면 개행 문자도 같이 출력


### 👉 한 줄로 입력받기
예시코드
```python
import sys
arr = []

a = int(sys.stdin.readline())
a.append(arr)
print(arr)
```
출력결과
```
>>> ['hello World\n']
```

- input() 함수와 같이 int(), float() 등 원하는 데이터형 변환 함수 안에 readline() 를 넣어준다.


### 👉 여러줄 입력받기
예시코드
```python
import sys

a = sys.stdin.readline().strip()
b = sys.stdin.readline().strip('\n')
c = sys.stdin.readline().rstrip('\n')
```
- `strip()`은 해당 문자열의 양쪽끝에 개행문자(\n) 공백(\t)을 삭제해준다.
- `rstrip()`은 문자열의 오른쪽에 모든 조합을 제거한다. 따라서 마지막 줄에서는 rstrip()을 써주었다.

### 👉 한 줄에 여러 개 입력받기
예시코드
```python
import sys

N, M = map(int, sys.stdin.readline.split())
```
- `input()`과 같이 `split()` 함수를 사용해서 나눠준다.
- 만약, 정수형으로 입력받고 싶다면 `map()` 함수를 사용한다.
  
### 👉 마무리
사용법을 알아보면서 `input()` 함수와 전체적으로 받는 틀은 같다고 생각했다.   
지금은 `input()`이 익숙하지만, 코드의 런타임을 생각한다면 앞으로 이 방법으로 입력 받아야겠다.  