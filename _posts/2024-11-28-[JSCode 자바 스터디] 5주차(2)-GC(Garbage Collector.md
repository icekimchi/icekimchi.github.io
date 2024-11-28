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
- GC가 다른 JVM 프로그램 실행이 멈추는 이유는 메모리 안정성 보장 때문이다.

### 👉 GC 모니터링

- GC의 성능 문제나 메모리 부족 문제를 사전에 파악하기 위해 모니터링이 필요하다.
- Young 영역에 있는 객체를 Old 영역에 언제 얼마나 이동했는지, stop-the-world가 언제 얼마나 일어났는지에 대한 정보를 알 수 있음

### 👉 GC 모니터링

#### jstat

- HotSpot JVM에 있는 모니터링 도구이다.
- jstat은 GC수행정보 뿐 아니라 클래스로더 수행정보나 Just In Time 컴파일러 수행정보도 알 수 있다.
- jstat은 $JAVA_HOME/bin 디렉토리에 있다.

#### -verbosegc 옵션

- Java애플리케이션을 가동할때 지정하는 JVM옵션 가운데 하나이다.
- 시작할 때 -verbosegc옵션을 지정해야 한다.
- 직관적으로 이해하기 쉬운 출력결과를 GC가 발생할 때마다 보여준다.

### 👉 out of memory 에러가 발생했을때

- OOME가 발생한다면 먼저 에러 로그를 통해 정보를 확인한다.
  **Exception in thread "main":java.lang.OutOfMemoryEeror: Java heap spac**
- Heap size의 부족으로 heap에 할당하지 못한 경우
  **Exception in thread "main":java.lang.OutOfMemoryEeror: PermGen space**
- 애플리케이션에서 너무 많은 class를 로드할 때 발생한다.(설계/구현에 의한 발생)
  **Exception in thread "main":java.lang.OutOfMemoryEeror: Reqeusted array size**
- 사용할 배열의 사이즈가 VM에서 정의될 사이즈르 초과할 때

### 👉메모리 누수를 어떻게 확인할 것인가요?

우선, 메모리 누수가 발생하기 전에 `객체 참조/리소스 해제`, `캐시` 등 좋은 코딩 습관을 가지려 노력할 것입니다. 하지만, 발생했다면 jstat으로 JVM의 heap Memory 상태를 확인하거나 힙 덤프 분석하여 발생 원인을 찾으려 할 것입니다.

### 참고

- https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC
- https://uchupura.tistory.com/222
- https://codingdreamtree.tistory.com/16
- https://www.nextree.co.kr/p3878/ -https://junuuu.tistory.com/771
