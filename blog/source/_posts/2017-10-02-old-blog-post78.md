---
title: 동현이형이랑 스터디 내용 정리
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 13:25:25
categories:
- Tip's
tags:
---
##### Java type
- primitive type : 8개
- byte > Byte = 8bit
- boolean > Boolean
- char > Character
- int > Integer
- short > Short
- long > Long
- double > Double
- float > Float
- primitive type 하고 wrapper type은 다르다는 점을 인지하고 넘어가는것이 좋다.
- primitive type의 예로 int가 있고, wrapper type의 예로 Integer가 있다.

##### 깔끔하면서도 성능이 좋은 코드?
- 반복문 형태는 for, while, do-while, 재귀호출이 있다.
- 재귀호출의 경우 성능상 좋지 않기 때문에 많이 쓰이지 않는다.(메소드를 호출하는 경우 리소스가 많이 잡는다)
- .하고.. 붙는 경우 연산을 한번 더 하게 된다. (ex:list.size())
- list.size()보다는 밖에 변수에다가 int size = list.size()로 밖에다가 선언해서 사용.

##### encaptulation(캡슐화)
- 일반적으로 private로 선언해서 사용하는것이 좋다.
- public은 공개적으로 사용해야 하는 경우에만.. 예들 들어 interface의 경우에는 public으로.. default로 public이 되어 있지만 public으로 선언하는것이 좋다.

##### 변수의 종류
- 공용변수 : static으로 선언되서 모든 Java단에서 사용하는 변수
- 전역변수 : class안에 선언되서 해당 Class안에서 사용하는 변수
- 지역변수 : method안에 선언되서 그 method안에서만 사용하는 변수  
Util에서 다른 부분에서 많이 사용을 하는데 인자값만 달리 들어오는 경우 static으로 메소드를 선언해서 사용하는것이 좋다.(ex:Stringutils)

##### if~else
- if(xxx){} 문에서 xxx안에 들어가는 !(not)을 쓰지 않는 것이 좋은습관이다.
- 만약에 not을 써야 하는 경우가 꼭 있다면 메소드로 따로 빼서 사용하는것으로..  
ex: ``!(a<list.size())``라고 if문 안에 들어가는 조건을 isUpperSize()라는 메소드를 만들어서 그 안에 사용하는것이 보기에도 좋다.(명확한 정도)
- 연산자 방향이 일관성있게 하는것이 보기에 좋다.  
ex : ``a < b && c < d`` 이런식으로..

##### String / StringBuffer / StringBuilder
- 성능(속도) : StringBuilder > StringBuffer > String
- 안전성 : StringBuffer > StringBuilder > String
- StringBuilder와 StringBuffer의 차이점은 Thread가 싱글이냐 멀티냐의 차이.
- StringBuilder, StringBuffer에서 추가를 할 경우에는 + 식으로 하는게 아니라 append 시켜야 한다.
- StringBuilder나 StringBuffer를 str로 선언을 했을때 리턴 받을 경우에는 return str이 아닌 return str.toString()으로 해야 한다.
- String str = "a" + "b" + "c"; 이런식으로 사용해도 된다. (Java버전 1.5나 1.6에서 StringBuilder에 append시켜줘서 처리를 하기 때문에 상관없다)

##### Framework
- IOC, DI(이 2가지 부분에 대한 개념 정리 한번 더 필요)
- IOC : Class의 매직넘버를 방지하기 위해 사용.
(IOC,DI - ApplicationContext의 Bean이 등록이 되어 있으면 가져다 사용할 수 있는 관계를 생각해볼것)
- 매직넘버 : 계속적으로 반복해서 사용하는 상수를 지칭.
- 토비 스프링 1장부분에서 해당 개념부분에 대해서 한번 읽어보면 도움이 됨.

##### Thread
- session의 경우 Thread pool의 지역변수.
- Java초기에는 Thread의 pool의 환경을 설정을 생각해주면서 코딩을 했지만, 지금은 따로 해주지 않아도 되는 부분 때문에 신경쓰지 않고 코딩.
- DB pool도 마찬가지로 Thread로 되어 있다.
- Concurrent -> Thread safe?
- ConcurrentHashMap의 경우 Thread의 제한을 두게끔 하는 부분????
- Iterator, static의 경우 예를 들어 다시 한번 생각.
- MultiThread를 생각할때는 Concurrent라는 키워드를 기억하고 있으면 된다.
- Syncronized 선언에 대한 시점도 생각을 해봐야 한다. 지금 현재 사용하는 곳은 static쓰는 부분에서만.
- Reverse AJAX 에서 살펴보면 폴링, 롱폴링에 대해서 알고 있어야 하는데 이 폴링하고 롱폴링이 Thread의 예제로 생각해볼 수 있다.
- Reverse AJAX는 최초 오는 req를 받고 res를 받으면 바로 다시 req를 보내주는 방식으로 알아서 계속 res를 보내주는 방식.
그냥 AJAX는 req를 사용자가 계속 보낼때마다 그 때 그 때 res를 보내주는 식이라고 생각을 하면 된다.  
즉, AJAX와 Reverse AJAX의 차이는 req와 res의 순서가 역전이 되기에 그렇게 명칭이 붙여졌다고 생각하면 쉽지 않을까?
