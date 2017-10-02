---
title: 이클립스(Eclipse) PermGen space 오류 관련 해결법
thumbnail: /images/ide_thumbnail.jpg
date: 2017-10-02 12:22:16
categories:
- Programming
- IDE's
tags:
---
이클립스 ini파일 내용중에서 -vmargs 아래줄 부터 아래와 같이 추가한다.

-Xverify:none  
-XX:+UseParallelGC  
-XX:PermSize=256M  
-XX:MaxPermSize=512M  
-XX:MaxNewSize=128M  
-XX:NewSize=128M  
-Xmx1024M

이클립스 실행후에 서버 설정을 마치면 아래 순서로 진행한다.  
1. Servers의 톰캣 더블 클릭.
2. Overview의 General information에서 Open launch configuration 을 클릭.
3. Argument 탭에 VM Argument 부분에 아래와 같이 추가로 입력한다.  
< 추가안 1 >  
-Xms1024m -Xmx1024m  
-XX:NewSize=256m -XX:MaxNewSize=256m -XX:PermSize=256m  
-XX:MaxPermSize=256m  
< 추가안 2 >  
-XX:MaxPermSize=256m -Xms512m -Xmx512m
