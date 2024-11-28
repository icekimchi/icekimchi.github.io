---
title: "[JSCode 자바 스터디] 5주차(2) - Gc(Garbage Collector)"
date: 2024-11-28 20:00:00 +0900
categories: [CS, JAVA]
tags: [JAVA, 자바, hashmap, map]
---

# 📌 GC(Garbage Collector)

### GC

- GC란 JVM Heap 영역에서 필요없는 메모리 객체를 정리해주어 메모리를 관리하는 기능입니다.

### 👉 장단점

장점

- 메모리 관리를 해주어 메모리 누수 문제를 관리하지 않아도 된다.
  단점
- GC를 수행하기 위해 다른 JVM 프로그램 실행이 멈춰 오버헤드가 발생할 수 있다.(Stop-The World 라고 한다.)

### 👉 Execute Engine

- . class파일과 같은 ByteCode를 실행 가능하도록 해석한다.

### 👉 JVM 메모리 영역

#### Method Area(메서드 영역)

- 클래스 정보를 처음 메모리 공간에 올릴 때 초기화되는 대상을 저장하기 위한 메모리 공간이다. 이 공간에는 Runtime Constant Pool도 존재하며, 상수 자료형을 저장하고 참조하는 역할을 한다.

#### Heap(힙)

![alt text](/images/자바스터디/힙구조.png)

- 객체를 저장하는 가상 메모리 공간이다. new 연산자로 생성된 객체과 배열을 저장한다.
- 모든 스레드가 힙 영역을 공유한다.
- JVM의 GC(Garbage Collector)가 이 영역을 관리한다.
- Young/Old Generation:
  > Eden : 객체들이 최초로 생성되는 공간
  > Survivor 0/1 : Eden에서 참조되는 객체들이 저장되는 공간
- Old 영역 : Eden 영역에 객체가 꽉 차면 첫 번째 GC가 발생한다. Eden 영역에 있는 값들을 Survivor 1영역에 복사하고, 이 영역을 제외한 나머지 영역의 객체를 삭제한다.

#### Stack(스택)

- 프로그램 실행과정에서 임시로 할당되었다가 메소드를 빠져나가면 바로 소멸되는 특성의 데이터를 저장하기 위한 영역이다.

#### PC Register

- Thread가 시작될 때 생성되며 스레드마다 하나씩 존재한다.
- 현재 수행 중인 JVM 명령의 주소를 갖는다.
