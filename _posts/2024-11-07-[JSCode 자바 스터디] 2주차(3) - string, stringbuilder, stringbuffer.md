---
title: "[JSCode 자바 스터디] 2주차(3) - string, stringbuilder, stringbuffer"
date: 2024-11-07 23:00:00 +0900
categories: [CS, JAVA]
tags: [JAVA, 자바, hashmap, map]
---

# string, stringbuilder, stringbuffer

### 👉 String literal과 new String(””) 차이

먼저, 두 방법 모두 자바에서 문자열을 선언하는 방식입니다.
두 방식은 메모리가 할당되는 영역에서 차이점이 있습니다.
![멘붕](/images/자바스터디/스택,%20힙.png)

- String은 힙 영역 안에 있는 String Constant Pool에 위치하지만, new String으로 선언 시에는 Heap 영역에 새로운 객체로 생성하게 됩니다.
- String 리터럴 방식으로 두 변수를 같은 문자열로 생성한다면, 객체는 하나만 생성되며 두 변수는 같은 변수를 가리킵니다. 따라서, equals() 연산과 == 연산 모두 같다고 나오게 됩니다.
- 하지만, new 연산자를 사용할 경우 두 변수는 문자열이 같더라도 다른 객체로 생성되어 ==연산에는 다른 주소를 참조하기 때문에 false를 리턴합니다.

### 👉 String, StringBuilder, StringBuffer 차이

세 클래스 모두 문자열을 저장하고 관리하는 클래스입니다.
하지만, String은 immutable(불변성)을 가진다는 점에서 나머지 두 클래스와 다릅니다. Heap 영역에 한 번 생성되면 변하지 않고, 기존의 객체가 제거되면 가비지컬렉터가 회수하는 방식입니다.

StringBuffer와 StringBuilder 모두 AbstratStringBuilder라는 추상메서드를 상속받아 구현하여 제공하는 메서드가 서로 동일합니다. 하지만, StringBuffer는 `동기화`를 지원하지만 StringBuilder는 동기화를 지원하지 않는다는 것이 다릅니다.

StringBuffer는 `Synchronsized` 키워드를 사용해 멀티 스레드 상황에서도 사용할 수 있습니다. 하지만, 이 동기화 때문에 StringBuilder보다 속도와 연산이 느리다는 단점이 있습니다.

따라서, 문자열과 스레드의 상황에 맞는 사용이 필요합니다.
