---
title: "[JAVA] Scanner 입력 알아보기"
date: 2024-7-22 23:00:00 +0900
categories: [Algorithm, JAVA]
tags: [JAVA, 자바, hashmap, map]
---

# Scanner

자바로 코딩테스트를 공부하게 되면서 입출력 방법부터 다시 공부하기로 하였다.   
자바의 입력받는 방법인 Scanner에 대해 알아보고자 한다.

### Scanner란?

- java.util.Scanner
- 파일, 문자열 등 다양하게 데이터를 읽어들일 수 있다.
- 대량으로 처리 시에는 느려 수행시간에서 비효율적이다.

#### Scanner 메서드
1. nextInt()  
    - 구분자는 공백문자 (space, tab, \n)
2. nextDouble()   
   - 구분자는 공백문자 (space, tab, \n)
3. next()   
   - 구분자는 공백문자 (space, tab, \n)
4. nextLine()   
    - 구분자는 개행문자(\n)
  
만약 입력으로 "Hello World\n"을 입력했을 떄   
next()는 `Hello`, `World` 이렇게 각각 단어만 받을 수 있고   
nextLine()은 `Hello World` 이렇게 문장으로 띄어쓰기를 포함하여 받을 수 있다
   


#### next()

```java
Scanner sc = new Scanner(System.in);
System.out.println("정수, 실수, 문자열을 차례로 입력하세요.");

System.out.println("읽은 정수: " + sc.nextInt());
System.out.println("읽은 실수: " + sc.nextDouble());
System.out.println("읽은 문자열: " + sc.next()); //White space를 만나면 종료
```
- next()는 구분자(white space) 직전까지 값을 읽은 후 유효문자만 출력한다.
- "안 \n녕\n" 일 때, "안(공백)\n" 에서 안까지 읽는 것이다.


#### nextLine()
```java
Scanner sc = new Scanner("하 \n이\n");
System.out.print("nextLine() 출력값 : \""+sc2.nextLine())
```
- nextLine()는 구분자로 "\n"을 인식한다.
- 위의 경우일 때는 "하(공백)\n"에서 하(공백) 을 읽는 것이다.
 
#### next, nextLine() 함께 사용

```java
Scanner sc = new Scanner(System.in);
System.out.println("나이 : " + sc.nextInt());
sc.nextLine(); //남아있는 구분자 제거
System.out.println("이름 : " + sc.nextLine());
```
- C언어를 공부했다면 값을 입력받을 때, 뒤에 "\n"을 삭제해줬던 것을 기억할 것이다.
- nextLine()를 사용해 구분자(\n)을 삭제할 수 있다.

