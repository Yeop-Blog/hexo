---
title: Java Fundamental 정리 - MVC, 고립화, Class, Instance, this
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-27 23:14:00
categories:
- Language
- Java
tags:
---
- **MVC**  
\- MVC 패턴 : Model, View, Controller로 돌아가게끔 설계를 하는 패턴(?)
<br>
- 고립화 : 접근제어 - 원본 보호를 위해
<br>
- Class와 Instance의 차이점(선언시)  
\- **Class : Static이 가능하다. 바로 사용 가능. 선언 1, 공유가 가능.**  
\- **Instance : Static이 불가능. new로 선언해야 함. new 횟수에 비례함. 공유가 불가능(고립)**  
< Class에서 Instance로 접근하는것은 금지(시점이 다르므로) >  
\- 전역변수 → Property(Java), C++에서는 멤버변수의 의미.  
\- 전역함수 → Method(Java), C++에서는 멤버함수의 의미.
<br>
- **this**  
\- 수첩마다 존재. 여기서 말하는 수첩은 Class라고 봐도 될듯.  
\- 절대적인 값이 아닌 VM이 알고있는 Class의 시작 주소, 가장 가까운 곳을 가리킴.
