---
title: Java Fundamental 정리 - 개발환경, 설정
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-25 23:01:00
categories:
- Language
- Java
tags:
---
- 개발환경
\- JRE : Java Runtime Environment. 흔히 말하는 자바 런타임 환경. [[다운로드]](http://www.java.com/ko/download/chrome.jsp?locale=ko&host=www.java.com)  
\- JDK : Java Development Kit. 자바 개발 도구. 자바로 개발하려면 필수로 설치. [[다운로드]](http://www.oracle.com/technetwork/java/javase/downloads/index.html)  
\- IDE : Integrated Development Environment. 통합 개발 환경. 여기서는 Eclipse가 한 예이다. [[다운로드]](http://www.eclipse.org/downloads/)  
**<설치 순서는 JRE → JDK → IDE 순으로 설치하면 된다>**

* 되도록 **폴더는 아래와 같이 정해서 설치** 하면 나중이 편하다!  
c:/Develop/(프로젝트명)/jdk  
c:/Develop/(프로젝트명)/jre  
c:/Develop/(프로젝트명)/ide  
<물론 각 폴더명에 맞게 jdk, jre, ide를 설치>  

- 이클립스 설치후 **workspace폴더** 역시 아래와 같이 정해두면 좋다!  
c:/Project/(프로젝트명)/workspace

* **이클립스 설치후 아래와 같이 설정** 을 맞추고 시작하면 매우 좋다!(이클립스 환경설정)  
\- 환경설정은 Window - Preferences로 들어감.  
General - workspace - Text file encoding - other에 EUC-KR  
General - workspace - New text file line delimeter (서버 환경 설정에 맞춰야 함)  
General - Editors - Text Editors - Displayed tab width (보통 4 or 2)  
General - Editors - show line numbers 체크 (옆에 숫자가 표시 되게끔 하는것)  
General - Content types - Text - Java Source File - Default encoding에 EUC-KR 입력후 Update 클릭  
Java - installed JREs 에서 jdk설정  
Java - Compilers 에서 level을 jdk버전에 맞게 설정

- **Project, Package, File, 변수**  
\- Project 이름 : 각 프로젝트 이름에 맞게끔 알아서~ (ex : JDK_01_IO)
\- Package 규칙 : 회사명.부서명.프로젝트명.모듈명 순으로 폴더 구조 처럼 정하는것이 좋다. 소문자로 할것. (ex:net.bit.lecture)  
\- File 이름 : 각 성격에 맞는 파일명을 쓸 것. (ex : IOExecuter, BoardExecuter)  
\- 변수의 경우 소문자로 시작. (ex : boardExecuter)
