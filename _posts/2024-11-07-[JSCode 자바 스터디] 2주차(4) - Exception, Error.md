---
title: "[JSCode 자바 스터디] 2주차(4) - Exception, Error"
date: 2024-11-07 23:00:00 +0900
categories: [CS, JAVA]
tags: [JAVA, 자바, Exception, Error]
---

# Exception, Error

### 👉 Exception과 Error의 차이

<공통점>

- Exception과 Error는 모두 Object 클래스를 상속한 Throwable 클래스를 상속 받는다는 공통점이 있습니다.
- Throwable 클래스는 getMessage()와 printStackTree() 메서드가 있어 오류나 예외에 대한 메시지를 확인할 수 있습니다.

<오류>

- 오류는 코드의 문제가 아닌 하드웨어 장비나 가상머신, 메모리와 같은 Unchecked Exception만을 뜻합니다. 따라서, 예외와 다르게 개발자가 미리 예측하여 방지할 수 없습니다.

<예외>

- 예외(Exception)는 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생합니다. 오류와 달리 개발자가 미리 예측해 방지할 수 있기에 상황에 맞는 예외처리를 해야 합니다.
- 알맞는 예외처리를 통해 프로그램이 종료되지 않고 정상적으로 작동되게 만들 수 있습니다. 또, 예외처리는Try Catch문으로 할 수 있습니다.

### 👉 Checked Exception과 Unchecked Exception의 차이

Checked Exception

- Exception의 종류인 Checked Exception은 예외처리가 필수이며, 처리하지 않으면 컴파일이 되지 않는 예외입니다. 따라서 컴파일 단계에서 명확하게 확인이 가능합니다.
- try-catch문으로 강제로 예외처리를 해주거나 예외가 발생하는 메서드에서 throws 예약어를 통해 호출한 메서드에 전달하는 방법으로 처리가 가능합니다.

Unchecked Exception

- Exception에 대한 체크를 하지 않아도 애플리케이션 코드를 실행할 수 있는 Excetpion입니다.
- RuntimeException을 상속받으며 런타임 환경에서 실행되면서 Exception이 발생합니다. 따라서 throws 예약어를 통해 명시적인 예외처리를 하지 않아도 됩니다.

> 인터넷을 참아보면서 두 Exception의 차이점이 컴파일, 런타임 단계에서의 오류라는 글을 보게 되었다. 그치만, 궁금해서 찾아보니 그것은 사실이 아니었다.

    두 예외 모두 런타임 과정에서 일어난다. 하지만, Checked 같은 경우에는 컴파일러가 예외처리를 하는 과정에서 코드가 실행되지 않기 때문에 컴파일 환경에서 발생하는 것처럼 보일 뿐이다. try-catch 로 강제 예외 처리를 해줘야 하기 때문에 그렇게 보이는 것일 뿐! 이라는 것을 기억해야겠다.

### 👉 throw와 throws의 차이?

- throw는 예외를 강제로 발생시켜 상위 블럭이나 catch문으로 예외를 던지는 방식입니다.

- 반면에 thorws 는 예외가 발생했을 때, 자신을 호출한 상위메서드로 예외를 던져 책임을 호출하는 쪽이 책임지도록 하는 방식입니다.

### 👉 try~catch~finally 구문에서 finally의 역할은?

- try 블록에서 일어난 일에 관계없이 무조건 실행될 코드
- 이 코드는 try 블록이 어떻게든 종료되면 실행된다
- return, continue, break 또는 throw 문을 사용해 제어를 이동시킬 수 있다.
- 제어가 이동되는 경우에는 해당 블록 이후의 제어 이동은 취소되고, 새로운 제어로 이동한다.

### 출처

https://webclub.tistory.com/71
