---
title: Java Fundamental 정리 - 전역변수, 지역변수..
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-25 23:27:00
categories:
- Language
- Java
tags:
---
* { ... } : 수첩이 생김과 동시에 주소가 생김. 사용할 때는 범위가 중요!
<br>
* 주소를 안다는 것은 변수를 안다는것과 동일.
<br>
* 검색시 초기 인덱스값은 -1, 찾으면 0 이상의 값.
<br>
* index와 sequence는 엄연히 다른 의미의 값.
<br>
* 재사용성  
1) Copy & Paste  
2) 코드에 주소를 매기기. ex) go to  
&nbsp;&nbsp;&nbsp;&nbsp;Scope(범위)를 맞춰야?(불일치가 되므로)
<br>
* Project 원하는것 우측 클릭후 Export(Project 추출), Import(Project 입력)해서 사용.
<br>
* 전역 변수(Global Variable) : 공유를 위해 쓰는 변수, 프로그램의 시작에서 끝까지 쭉~
* 지역 변수(Local Variable) : 한 스콥({...})안에서만 사용을 하고 끝내는 변수
* 각 변수의 장단점  
\- 전역변수의 장점 : 공유가 쉽다. / 단점 : 보안이 좋지 않음.  
\- 지역변수의 장점 : 보안이 좋음. / 단점 : 공유가 어렵다. (뭐 당연한 이야기겠지만..;;)  
**<어떤 변수를 쓸지 결정하는것은 분석 때 결정을 하면 된다>**  
\- 지역변수 임에도 공유를 할 경우  
: 파라미터(전달). OS가 값을 가져다가 넣어줌. ex) regist(int sequence)
<br>
* 메소드 형 선언  
\- void 형 : null만 담을 수 있는 것.  
\- static 형 : 정적 선언. 당연히 이것이 붙지 않으면 동적 선언. (Java가 동적이기 때문에~)
