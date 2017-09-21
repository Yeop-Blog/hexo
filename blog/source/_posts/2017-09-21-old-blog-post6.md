---
title: 1. Servlet
thumbnail: /images/java_thumbnail.jpg
date: 2017-09-21 21:06:05
categories:
- Language
- Java
tags:
---
##### 1장. 서블릿과 JSP는 어디에 쓰이는 것인지 알아보자.
- 웹 서버 : 클라이언트로부터 요청을 받아 요청한 것을 넘겨주는 역할
- 클라이언트 : 사용자가 서버에 요청을 보낼 수 있는 기능을 제공할 뿐더러 서버가 보내온 요청의 결과를 화면에 출력하는 역할까지 담당.
- HTTP : Hyper Text Transfer Protocol. TCP/IP 기반에서 요청,응답(Request/Response)을 전송하는 프로토콜
- HTML : HyperText Markup Language.
- 단순한 요청은 GET, 사용자가 입력한 정보를 함께 보내려면 POST로 보내라.
- URL : Uniform Resource Locators  
http:// --> 프로토콜  
www.wickedlysmart.com:80/ --> 서버, IP주소  
beeradvice/select/ --> 서버에서 자원 위치  
beer1.html --> 자원  
- 뒤에 포트 숫자의 경우 고정적으로 쓰이는 부분이 있다.  
21 : FTP / 23 : Telnet / 25 : SMTP / 37 : Time / 80 : HTTP / 110 : POP3 / 443 : HTTPS
- CGI : Common Gateway Interface  
사용자가 서버에게 웹페이지를 통한 요청이 있었을 때, 그것이 응용프로그램에 의해 처리 될 필요가 있다면 서버가 응용프로그램을 실행시키고 필요한 메시지를 받는다. 이 때 서버와 응용프로그램 사이에 데이터를 주고 받기 위한 표준화된 방법을 CGI라고 한다. (네이버 백과사전 참고)  
- Servlet  
서버에서 수행되는 소형 프로그램. 일반적으로 서버에 존재하며 사용자 입력에 의해 데이터베이스에 접근하는 프로그램은 공통 게이트웨이 인터페이스(CGI) 프로그램을 사용해 수행되는데, 자바 서버 프로그램은 자바 프로그래밍 언어로 수행된다. CGI 프로그램보다 수행 속도가 빠르고, 프로그램 프로세스가 생성되는 것이 아니라 각 사용자 요청이 상주 프로그램(daemon)의 하나의 스레드(thread)로 수행된다. 추가(add-on) 모듈로 된 자바 서블릿은 넷스케이프 엔터프라이즈와 인터넷 정보 서버(IIS), 아파치 서버에서 수행된다. (네이버 백과사전 참고)  
- Servlet 안에 모든걸 다 넣기에는 무모한 면이 있기에 그 부분을 해결하기 위한 방법으로 JSP를 사용.  
- JSP는 HTML안에 자바를 넣을 수 없을까라는 고민에서 탄생.  

##### 2장. 웹 어플리케이션 구조
- 컨테이너가 주는 혜택 : 통신(커뮤니케이션) 지원, 생명주기 관리, 멀티스레딩 지원, 보안이 유용, JSP 지원
- 컨테이너가 돌아가는 방식  
1) 사용자가 링크를 클릭합니다.  
2) 서블릿은 HttpServletRequest, HttpServletResponse 객체를 생성합니다.  
3) 어떤 요청인지 분석하여 알아내고 그에 맞춰서 service() 메소드를 호출, do Get()/do Post() 둘 중 하나를 결정합니다.  
4) doGet()/doPost() 중 하나를 생성후 Response 객체에 실어 컨테이너에 보냅니다.  
5) 스레드 작업이 마치면 Request와 Reponse객체를 소멸시킵니다.  
- 배포 서술자(Deployment Descriptor)라는 XML파일에서 서블릿과 URL을 서로 매핑이 가능하다.
- 서블릿 > 서블릿 + JSP > 서블릿 + JSP + Model = MVC패턴(Model+View+Controller)

##### 3장. 초 간단 미니 MVC 튜토리얼
- 예제를 통해 서블릿을 구현해보는 부분이므로 패스.

##### 4장. 서블릿이 되어 보자
- 서블릿의 주기 : 클래스 로딩 -> 생성자 실행 -> init() -> service() ->  destory()
- init() : 서블릿 인스턴스 생성뒤 바로 호출. service() 메소드 전에 실행. 딱 한번만 실행.
- service() : 클라이언트의 요청을 받았을때.
- destory() : 서블릿이 죽기 전에 실행. 딱 한번만 실행.
- 서블릿 초기화  
 1. ServletConfig 객체 : 서블릿당 하나, ServletContext에 접근하기 위해 사용, 파라미터값은 DD에서 설정 가능.  
 2. ServletContext 객체 : 웹 애플리케이션당 하나, 웹 앱의 파라미터값을 읽어오기 위해 사용, 서버정보를 파악하기 위해 사용.  
- GET : URL로 자원 또는 파일을 달라고 요청.
- POST : Request에 첨부한 몸체 정보를 서버로 보내, 요청한 URL로 정보를 요구. 부가정보를 가진 GET과 비슷.
- HTTP 스펙 1.1 에서는 GET, HEAD, PUT은 멱등이라고 정의.
- method="POST"라고 코딩하지 않을 경우 기본은 GET이다.
- Request 객체에서 파라미터를 뽑아 내기 위해 getParameter("파라미터 이름") 메소드를 호출, 리턴값은 String.
- 파라미터 값이 여러개인 경우에는 getParameterValues("파라미터 이름") 메소드를 사용, 리턴값을 String[].
- Response는 리다이렉트(Redirect)와 디스패치(Dispatch)로 구분이 된다.
- Redirect : 요청을 완전히 다른 URL로 방향을 바꿀 수 있다. 즉, 주소가 바뀐다.
- Dispatch : 웹 애플리케이션에 있는 다른 컴포넌트(JSP)에게 처리를 위임. 주소가 바뀌지 않는다.
- sendRedirect : session 정보를 유지한채로 Redirect하는 것. Response한 후에는 할 수가 없다. 매개변수로 URL객체가 아닌 String 객체를 받음.

##### 5장. 웹 애플리케이션
- 서블릿 초기화 된 다음에 서블릿 초기화 파라미터를 사용할 수 있다. ex)ServletConfig
- 컨테이너는 서블릿을 초기화 할때 '단 한번만' 초기화 파라미터를 읽습니다.
- 초기화 파라미터는 컨텍스트 초기화 파라미터가 유용하다. ex)context-param
- 초기화 파라미터 = 정해진 상수라고 생각하는것이 좋다.
- 초기화 파라미터를 저장하기 위해서 리스터를 구현하여 사용. 리스너가 아니면 String밖에 저장이 안됨.
- 리스너 작성 및 사용 : 리스너 클래스 생성 -> 클래스 배포 -> 배포 서술자에 항목 추가
- 속성(Attribute)과 파라미터는 엄연히 다르다. 가장 큰 차이점은 리턴타입이 속성은 Object이고, 파라미터는 String이다. 그 외에 대한 차이점은 Headfirst P220쪽 참고!
- 3가지 생존범위 : Context, Request, Session + @로 Page까지 있음.
- Context는 누구나 접근이 가능하다.
- Request는 Garbage 통해서 접근후 response 처리후 날라감, 즉 초기화 됨.
- Session은 나만 접근, 즉 특정 HttpSession에 접근 권한을 가진 녀석만 접근이 가능.

##### 6장. 대화 상태 유지하기.
- 직접 적인 Session과 기타 리스너등에 대한 내용. 정리보단 이 장은 필요시 책을 한번 더 살펴보는게 나을듯.
