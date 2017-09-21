---
title: 2. JSP
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-21 21:16:52
categories:
- Language
- Java
tags:
---
##### 7장. JSP가 되어 보자.
- 패키지 import하기 위해서는 page지시자를 이용.
- 스크립트 코드 : <% %>의 형식을 갖춘 코드.
- 표현식 : <%= %>의 형식을 갖춘 코드. 세미콜론(;)이 붙지 않는다.
- 선언식 : <%! %>의 형식을 갖춘 코드. 세미콜론(;)을 붙여야 한다.
- 내장객체 중에는 out만이 있는것이 아니다. ex) request, response, session, page 등등..
- 주석에는 2가지 종류가 있다.  
1) ``<!-- HTML Comment -->``  
2) ``<%-- JSP Comment %>``  
- JSP LifeCycle  
컨테이너 > web.xml > xxx.jsp > xxx_jsp.java > xxx_jsp.class > 메모리 로딩 > jspInit() 실행 > 서블릿화 > \_jspService() 메소드 실행(다음 실행시에는 일반 서블릿과 동일하게 처리)
- 속성범위에 대해서는 P345쪽 참고해서 볼것. page는 서블릿에서 제공하지 않음.
- **JSP안에 있는 자바 코드의 유지보수, 웹 페이지 디자이너가 Java라는 언어까지 알 필요 없다는 전제하에 나온 것이 EL**  
- EL의 기본 형식
``<%= application.getAttribute("mail") %>``와 ``${applicationScope.mail}``과 같다.
- EL을 무시하게 만들려면?  
1) DD에다가 ``<el-ignored>true</el-ignored>``태그를 추가 하는 방법  
2) ``<%@ page isELIgnored="true" %>`` page 지시자 속성을 추가 하는 방법

##### 8장. 스크립트가 없는 페이지
- MVC 애플리케이션은 속성으로 정보를 공유.  
서블릿 코드 : request.setAttribute("name", name);  
JSP(뷰) 코드 : request.getAttribute("name");  
- JSP에는 빈 관련 표준 액션이 존재.  
ex) ``<jsp:useBean>, <jsp:getProperty>, <jsp:setProperty>...``
- ``<jsp:useBean>``**은 빈은 선언하고 초기화 하는 태그**  
``<jsp:useBean id="person" class="foo.person" scope="request"/>``  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;표준 액션 / 객체 식별자 / 클래스 타입 선언 / 속성 생존범위
- ``<jsp:getProperty>``**은 속성 빈 프로퍼티를 읽어오는 태그**  
``<jsp:getProperty name="person" property="name"/>``  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;표준 액션 / 빈 객체 이름 / 프로퍼티 이름
- ``<jsp:useBean>``은 객체를 생성, 자신의 몸체(태그 안에 태그가 가능)를 가질 수 있다.
- 다형성 기법을 사용하려면 <jsp:useBean>태그에 type속성을 추가하면 된다.
- 클래스 없이 type을 사용이 가능하지만 생존범위 안에 존재하지 않으면 Exception이 발생.
- **scope속성의 디폴트 값은 page이다.**
- param속성을 사용하면 빈에 요청 파라미터를 설정할 수 있다.  
ex) ``<jsp:setProperty name="person" property="name" param="userName"/>``
- 더 나은방식은 필드 이름과 프로퍼티 이름이 동일하면 된다.  
ex) name="input type="text" name="name">으로 할 경우
``<jsp:setProperty name="person" property="name" />``으로 하면 된다.
- 빈의 모든 프로퍼티 이름과 요청 파라미터 이름이 같다면 아래와 같이 표현이 가능하다.  
``<jsp:setProperty name="person" property="*" />``
- **프로퍼티의 프로퍼티(내장 프로퍼티)를 출력하고 싶으면 어떡해야 할까?  
-> 답은 EL**  
```html
<html><body>  
Dog's name is : ${person.dog.name}  
</body></html>  
```
여기서 ``${person.dog.name}`` 부분은 ``<%= ((foo.person) request.getAttribute("person")).getDog().getName() %>``과 동일하다.
- .(도트)연산자를 이용하려면 왼쪽은 반드시 Map 또는 Bean이어야 한다.
- []연산자는 .(도트)연산자보다 기능이 막강하다.
- []연산자는 왼쪽에 Map, Bean, Array, List 변수들이 올 수 있다.
- []연산자 안의 값이 "..."으로 있다면, Map의 Key값이거나, 프로퍼티 또는 리스트의 배열 인덱스가 될 수 있다.  
ex) ``${musciList["something"]}``
- []연산자 사용하는 다양한 예  
1) Music is : ``${musicList}``  
2) First song is : ``${musicList[0]}``  
3) Second song is : ``${muiscList["1"]}``
- Bean과 Map일 경우 둘 다 사용 가능하다.  
ex) ``${musicMap.Ambient} = ${musicMap["Ambient"]}``
- []연산자 안에 내장 표현식을 사용할 수 있다.  
ex) ``${musicMap[MusicType[0]]} = ${musicMap["Ambient"]}``
- EL의 경우 null값을 산술연산에서는 0으로 논리연산에서는 false로 처리한다.
- 템플릿을 재활용하기 위해 사용하는 지시자로 include 지시자가 있다.
- 표준 액션 태그로는 <jsp:include>가 있다.
- include 지시자는 "변환"시에, ``<jsp:include>``는 "실행"시에 사용을 한다. response가 있는 JSP페이지의 경우 ``<jsp:include>``를 사용하는 것이 좋고, 처음부터 한번에 띄워도 좋을 경우에는 include 지시자를 사용한다.
- 재 사용할 페이지의 경우 ``<html>``,``<body>``, 시작, 마침 태그를 작성하지 않는것이 좋다.
- JSP 페이지를 넘길때 ``<jsp:forward>``조건부 포워딩 태그도 있음~ (p448 참고)

##### 9장. 막강한 커스텀 태그
- EL과 표준 액션 태그만으로 부족하여 나온것이 JSTL  
~~~
<c:out>
<c:forEach>
<c:if>
<c:choose><c:when><c:otherwise>
<c:set>
<c:remove>
<c:import>
<c:param>
<c:url>
~~~
- 위와 같은 다양한 JSTL을 사용하여 JSP페이지를 간단하게 코딩할 수 있다... 는데 영 -\_-;;; 어느정도 사용법에 대해서만 익히고 넘어가도록 하자.
- errorPage의 경우 DD(배포 서술자)에서 설정할 수 있다. (P.504 참고)
