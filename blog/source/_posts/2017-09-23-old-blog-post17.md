---
title: Java Fundamental 정리 - 문제인식, 정보수집, 분석
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-23 22:15:00
categories:
- Language
- Java
tags:
---
1. 문제인식
 - 범위에 따라 인식이 틀려짐
 - 재사용성이 중요(미리 예측이 가능해야 함)
 - Stake holder(이해 당사자)를 결정하는 단계 ← 이것에 따라 절차가 변경됨
 > 이해당사자란? -> 이득과 손해 보는 User들

2. 정보수집
 - 절차(Procedure) + Data
<br>
3. 분석(비서를 예로 들어서 생각하면 좋다)
 - 비서가 해야 할 일의 약속 = Protocol
 - Protocol? → TCP/IP, HTTP, FTP 등등..
 - Program = System
 - User = 말 그대로 사용자~
 - 용어집<여기서는 게시판을 예로 들어서 설명>  
 1) 메모작성 → 등록  
 2) 훑어보기 → 목록 조회  
 3) 자세히 보기 → 상세 조회  
 4) 메모 수정 → 수정  
 5) 버리기 → 삭제  
 6) 게시판 → 게시물 목록  
 7) 포스트잇 → 게시물 정보  
 - 조회 : 저장한 것을 갖고 오는 것(시작위치 알고 있음)

<등록>  
1) 사용자는 등록을 요청합니다.(Request)  
2) 시스템은 입력폼을 출력합니다.  
3) 사용자는 입력합니다(메모에 적는 것) - 내용, 제목 등등..  
4) 사용자는 처리를 요청합니다.  
5) 시스템은 데이터를 추출합니다. (입력한것을 갖고 오는 것)  
6) 시스템은 데이터의 유효성을 검사합니다.  
7) 시스템은 저장 처리를 합니다. (절차가 더 남이있다는 뜻)  
&nbsp;&nbsp;&nbsp;&nbsp;7-1) 시스템은 게시물 번호를 조회합니다.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-1-1) 현재 번호 조회  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-1-2) 번호 증가  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-1-3) 저장  
&nbsp;&nbsp;&nbsp;&nbsp;7-2) (데이터를)묶는다. → 다음번에 찾기 쉽도록..  
&nbsp;&nbsp;&nbsp;&nbsp;7-3) 저장  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-3-1) 현재 저장 위치 조회(게시물 번호가 X)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-3-2) 저장 위치 증가  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-3-3) 저장(위치 정보)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7-3-4) 저장(게시물 정보)  
8) 시스템은 등록 결과를 출력합니다.

<목록 조회> : 시작 주소를 통해 검색(loop, 판단문)  
1) 사용자는 목록 조회를 요청합니다.  
2) 시스템은 조회를 합니다.  
3) **시스템은 유효성 검사를 합니다.**  
4) 시스템은 목록을 출력합니다.  

<상세 조회>  
1) 사용자는 상세 조회를 요청합니다.  
2) 시스템은 입력폼을 보여줍니다.  
3) 사용자는 입력합니다.  
4) 시스템은 데이터를 추출합니다.  
5) 게시물 목록으로 이동합니다.(시작주소)  

\* 에러는 추출, 조회 에서만 걸러낸다.  
\* 유니크(Unique) - 고유번호  
\* 아이디(Id) = 시퀀스(sequence) = Auto increment(자동 증가) = 식별자  
\* 변수 선언은 loop밖에서 선언하는것이 좋다(메모리 부족현상 방지)  
\* 트리 구조는 검색, 링크 구조는 삭제에 적합하다.
