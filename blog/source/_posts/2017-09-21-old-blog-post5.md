---
title: String하고 String Buffer의 차이점
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-21 21:03:17
categories:
- Language
- Java
tags:
---
1.String : String은 각 객체를 만들때 생성을 하고 다시 새로운 문자를 추가하거나 할 때 기존의 값은 GC에 넘겨지고 다시 가르키기 때문에 메모리 속도면으로 볼 때 상당 시간이 걸린다.  
2.String Buffer : String과는 달리 공간을 만들어놓고 객체값이 변할때마다 그 공간에서 처리가 때문에 속도면에서 좋다.

그래서 String Buffer가 String보다 많이 쓰인다고 한다. 끗~
