---
title: Java Fundamental 정리 - Class, Instance, Construct, Java와 C의 차이.
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-27 22:54:00
categories:
- Language
- Java
tags:
---
- 로딩 역시 정적로딩, 동적로딩이 있다.
<br>
- 목적에 맞게 분리(File)  
\- Initialize : 대부분은 데이터의 초기화(설정), 할당  
\- File이 많아지면 Package
<br>
- 변수가 많아서 File로 분리(재사용이 가능하게끔) : class  
--> 분리 후 사용시 불러와 합쳐서 사용 : include
<br>
- import : include 중복을 방지하는 기능(File의 위치를 나타내줌)
<br>
- Class형 : 단순히 묶은거. (변수와 함수(function)의 조합?)  
\- 크기로 따진다면 int, char, byte 등등.. > void, function() > class 로 이야기 할 수 있을듯.
<br>
- Instance(객체) : 변수의 시작(선언), 종료(해제)를 정할 줄 알아야 함.  
\- new를 앞에 붙여서 생성을 한다.  
\- Static으로 선언된 것은 프로그램 시작시 바로 먼저 시작된다.  
그 외에는 new로 생성이 되야 한다.
- Construct(생성자)  
ex) Board() { ... } < 이런게 그냥 생성자이다. 끗~
<br>
- Java  
\- VM : Virtual Machine  
\- 변수 선언은 실제로???  
\- 변수 → Application → OS (변수 → OS는 바로 갈 수 없음)  
\- OS는 C언어 이기 때문에 변수명이 중복시 문제 발생.
- C와 Java의 차이점  
\- C의 경우 : xxx.c / xxx.h(헤더) ----------------------------------> OS  
Compile(소스를 절차화) = cc = gcc  
\- Java의 경우 : xxx.java ------(Compile = javac)------> VM ------(Compile = java(.class))------> OS
