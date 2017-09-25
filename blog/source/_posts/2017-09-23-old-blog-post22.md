---
title: Java Fundamental 정리 - InputStream, OutputStream, SVN설치
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-25 23:12:00
categories:
- Language
- Java
tags:
---
* 고정형 길이 : 짧으면 Stop. 적당히 입력하면 공간이 남은채로 진행.

* 읽기 → byte + byte = char → char[] → buffer

* 무언가를 시킴 ↔ 담기 ↔ 변환 ↔ 읽기

* Composition(구성, 조합) < Inheritance(상속)보다 더 중요! >

* 읽기는 무조건 InputStream. (메모리에서 1byte씩 읽어들이는것)(ex:byte)

* byte에서 변환 Reader(ex:char)

* 담는 부분 BufferedReader(ex:char[]), BufferedInputStream(ex:byte[])

* BufferedWriter -------> Writer -------> OutputStream  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(char[])&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(char)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(byte)

* BufferedReader -------> Reader -------> InputStream

* InputStream은 byte, Reader는 char.

* reader는 read를 1번 또는 2번 또는 n번 할 수 있다.

* flush() : 꽉 채우지 않더라도 뿌리라고 하는 메소드.

* Plug in 설치.  
\- Help - install new software - work with (helios~) 선택 - Collaberation - subversive SVN Team Provider - next 클릭(2번) - 동의후 Finish!

* 서버에서의 흐름에 대한 부분.  
\- commit : 서버에 바뀐 내용을 적용  
\- update : 서버에서 갖고와 내용을 변경  
\- merge : 병합  
\- conflict : merge 에러가 날 경우(?)

* SVN 설치후 적용  
\- window - Preferences - Team - SVN 클릭 - SVN kit 최신버전, Native JavaHL 최신버전 - Finish.  
(이후 show에서 SVN - SVN Repositories 선택하여 창을 보이게끔 하고 SVN 추가)
