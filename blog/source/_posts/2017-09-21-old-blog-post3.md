---
title: Java 리플렉션(Reflection), Static에 관하여…
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-21 00:22:03
categories:
- Language
- Java
tags:
---
* Reflection = 게시물 조회  
– 객체의 정보를 획득 + Invoke
* RMI : Remote Mehtod Invoketion  
메소드의 정보를 획득해 실행하는 것
* Class Name : ex) net.bit.lecture.board.BoardNo(그냥 BoardVO가 아님)
* Map의 해결방법 -> Reflection  
– 문자열을 갖고 객체를 생성하는 방법  
– Java Design Pattern, Framework를 공부하게 될 것  
→ 목표는 파일로 관리를 하는 것
---
* Static  
– Static 블럭 : 딱 1번만 동작하고 싶을때 사용 (여러개 메모리중에서)  
– Static 변수 : 자료구조의 변수인 경우 Static은 사용하면 안됨. 계속 메모리에 쌓이므로 조심해서 사용해야 함.  
– Static 메소드 : Static은 Static끼리 논다 -> 같은걸 매번 반환할 수 있다.  
– Static의 장점 : 공유!! → Singleton Pattern  

* Filed, Method에서만 쓰인다?  
→ 상태를 건드리지 않는 Method 전부 공유해서 쓰는 것.
