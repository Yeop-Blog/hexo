---
title: Java Fundamental 정리 - 아키텍처
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-23 22:34:00
categories:
- Language
- Java
tags:
---
- 입력 → 데이터 유지 → 처리
<br>
- 출력
<br>
- Computer 단계별 구조는 다음과 같다.  
 **OS > Application → API → Kernel → HAL**  
 \- OS : 하드웨어 제어를 위한 부분  
 \- HAL : Hardware Abstract Layer. 하드웨어 추상 계층.  
 \- API : Application Programming Interface  
<br>
- a = read();  
 \- a가 가르치는 위치의 값이 read의 값이 된다.(a가 read값이 된다는 것이 아님)  
 1) 임시 저장공간에 값을 대입  
 2) a의 위치 값으로 이동  
 3) 임시 저장공간 값을 위치 값에 넣음
<br>
- \r = CR = 13 , \n = LF = 10  
 \- 개행 문자의 경우 위와 같은 값을 가진다.
<br>
- **입력의 경우 전송에 있어서 4가지 규칙**에 따라 전송하는것이 좋다.  
1) 길이를 정하기  
2) 끝을 표시하기(ex:\n, 비슷한 방법으로는 null)  
3) 시간으로 끊기(무한대기에서 일정 시간대기후 끊게끔) → 이미지 파일을 예로..  
4) 미리 정보를 보내기(ex:헤더 파일)
<br>
- **출력의 경우 시작 주소**를 알면 됨.
<br>
- Type에는 여러가지 유형이 있다.
 - **boolean**(8bit = **1byte**)
 - **char**(16bit = **2byte**)
 - **byte**(8bit = **1byte**)
 - **short**(16bit = **2byte**)
 - **int**(32bit = **4byte**)
 - **long**(64bit = **8byte**)
 - **float**(32bit = **4byte**)
 - **double**(64bit = **8byte**)  
 <**위 자료형 외에는 모두 32bit = 4byte 자료형**이라고 생각하면 된다>  
 <**위 자료형 외에는 null값이 가능**하다> → 어딘가의 주소를 가르키지 않는다.>
