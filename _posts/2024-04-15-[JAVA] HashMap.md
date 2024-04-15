---
title: "[JAVA] HashMap 알아보기"
date: 2024-04-15 23:00:00 +0900
categories: [Algorithm, JAVA]
tags: [JAVA, 자바, hashmap, map]
---

# HashMap

자바 스프링을 공부하던 도중, 코딩테스트로 파이썬만 사용하다보니 hashmap 사용이 어색하여 개념을 다시 정리하려고 한다.

### HashMap이란?

- Map는 `key`와 `value`로 값을 저장하는 자료구조이다.
- `key`는 중복될 수 없다.

#### HashMap 생성

```java
HashMap<String, String> map1 = new HashMap<String, String>(); //HashMap 생성
HashMap<String, String> map2 = new HashMap<>();
```

#### HashpMap에 값 추가

```java
HashMap<String, String> map1 = new HashMap<>();
map1.put(1, "사과") //key와 value 추가
```

#### HashMap 값 삭제

```java
map.remove(1); //key가 1인 객체 삭제
map.clear(); //모든 값을 제거
```

#### HashMap 값 출력하기

- for문을 사용하여 key, value값을 모두 출력할 수 있다.

```java
for (String key: map.keySet()){
    System.out.println("key :" + key + "value :" +  map1.get(value));
}
```

#### 실제 사용 코드

- 예시코드 1

```java
private Map<String, ControllerV4> controllerMap = new HashMap<>();

public FrontControllerServletV4() {
        controllerMap.put("/front-controller/v4/members/new-form", new MemberFormControllerV4());
        controllerMap.put("/front-controller/v4/members/save", new MemberSaveControllerV4());
        controllerMap.put("/front-controller/v4/members", new MemberListControllerV4());
    }
```

- 예시코드 2

```java
private Map<String, String> createParamMap(HttpServletRequest request) {
    Map<String, String> paramMap = new HashMap<>();
    request.getParameterNames().asIterator()
        .forEachRemaining(paramName -> paramMap.put(paramName, request.getParameter(paramName)));
    return paramMap;
}
```
