---
title: Java Fundamental 정리 - 설계(Design)
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-25 22:45:00
categories:
- Language
- Java
tags:
---
##### 여기서 설계는 게시판을 예로 들어서 설명합니다.

* 기본적인 설계  
1) 사용자가 실행  
&nbsp;&nbsp;&nbsp;1-1) 자원 생성(어느 시점에서 변수 선언할지를 정함)  
<u>2) 인사말 출력 3) 메뉴 출력 4) 입력폼 출력</u>  
: 위 3가지 while(true) 무한루프로..  
5) 입력 + 처리요청  
6) 추출(b=a;)  
7) 유효성 검사(if)  
8) 분기(switch)  
9) 인사말 출력  
&nbsp;&nbsp;&nbsp;9-1) 자원 해제  
10) 종료  
<br>
* 설계에 따른 예제(설정)  
1-1) 자원 생성  
: boardList → char[][][], 길이는 9  
&nbsp;&nbsp;index → int = 0 (저장위치 설정)  
&nbsp;&nbsp;sequence → int = 1 (게시물 번호 설정)  
2) 인사말 출력  
: "게시물 관리 시스템 입니다.(엔터)" 출력  
3) 메뉴 출력  
: "등록 : R(엔터)"  
&nbsp;&nbsp;"목록조회 : L(엔터)"  
&nbsp;&nbsp;"상세조회 : V(엔터)"  
&nbsp;&nbsp;"수정 : E(엔터)"  
&nbsp;&nbsp;"삭제 : D(엔터)"  
&nbsp;&nbsp;"종료 : Q(엔터)"  
4) 입력폼 출력  
: "선택 : "  
5) 입력 + 처리요청  
: 메뉴를 선택, OS에 따라 틀림.  
6) 추출  
7) 유효성 검사  
: 여기서는 간단히 입력 유/무만 검사  
8) 분기  
9) 인사말  
: "안녕히 가세요.(엔터)" 출력  
9-1) 자원 해제  
: bufferedReader, bufferedWriter, inputStream, outputStream, reader, writer  
10) 종료
