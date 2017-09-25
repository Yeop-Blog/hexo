---
title: Java Fundamental 정리 - CRUD, 배열, 메모리, 자료구조
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-25 22:20:00
categories:
- Language
- Java
tags:
---
1. CRUD
 - C(Create) : 선언, 할당 부분.
 - R(Read) : 시작주소와 길이가 중요하다. (대입 연산자의 오른쪽)
 - U(Update) : 대입 연산자의 왼쪽
 - D(Delete) : 할당 부터 지워야 함! → 그 후에 선언 삭제.
<br>
2. 배열  
int[][] c;  
c = new int[2][];  
c[0] = new int[3];  
c[1] = new int[2];  
c[1][0] = 5;  
...  
int[][][] d;  
d = new int[2][][];  
d[0] = new int[2][];  
d[0][0][1];  
<자세한 내용은 4번째 수업에 대한 부분을 참고>  
<br>
3. 메모리  
\- CPU는 반복과 판단으로 이루어진다.  
\* 판단  
if() { } else { } / if() { } else if() { } else { }  
switch() { case x: case y: default: }  
\* 반복  
while() { } / do { } while();  
for(시작값; 증가치; 종료조건){ }  
<br>
4. 자료구조  
\- Create  
: index(0부터 이상의 값을 가짐) 등록 +1 / 삭제 -1, Tree구조는 등록이 느림(검색에 적합)  
\- Read  
: 검색(Search) → 정렬(Sorting) → 저장 위치(indexing(위치정보를 기억해두는))를 알아두어야 함(기준점) → 위치와 찾을값을 비교(분할기법)  
\- Update  
: 메모리 로드가 힘들어짐(?)  
\- Delete  
: 주소를 기억하는 방식(Linked List) ← 검색은 느리다.
