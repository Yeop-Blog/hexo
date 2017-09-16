---
title: Apache와 Tomcat의 차이
date: 2017-08-07 00:00:00
tags:
categories: Java
thumbnail: /images/java_thumbnail.jpg
---
- Apache : apache라는 소프트웨어 단체에서 만든 오픈소스 http web server
- Tomcat : was(web application server)라고 불리며, web server와 web container의 결합이라고 볼 수 있다.
- 차이점<br/>
– web server는 정적인 데이터를 처리, was는 동적인 데이터를 처리<br/>
– 즉, 단순 html, css 등 파일과 같은 리소스를 처리할 때는 web server를 활용하면 빠르게 처리가 가능<br/>
– DB와 연결되어 있거나 프로그램으로 데이터 조작이 필요한 경우 was를 활용
- 보통 tomcat 앞에 apache를 놓는 이유?<br/>
– 많은 개발자들이 애플리케이션 서버로 톰캣을 사용하는 경우에 스태틱 파일(css, js, html, 이미지)은 톰캣 앞에 아파치 웹 서버(Httped)를 두어서 처리하게 하는 것이 좋다고 생각한다. 외부 요청은 일단 Apache Httpd가 받고, 톰캣 내에서 처리할 자바 애플리케이션만 톰캣으로 다시 전달해서 처리하고 그 외의 리소스는 Apache Httpd가 직접 처리하게 만들어야 성능이 좋다고 생각한다. 자바로 만든 서버인 톰캣은 스태틱 파일 처리에서 Apache Httpd만 못하다는 것이 그 이유이다.하지만 톰캣과 Httped의 개발자에 따르면 이는 개발자들이 잘못 알고 있는 미신이다. 아직도 톰캣 3를 사용하고 있는 것이 아니라면 말이다.<br/>
톰캣은 5.5부터 Httpd의 native모듈을 사용해서 스태틱파일을 처리하는 기능을 제공한다. 이 경우 Httpd와 톰캣이 같은 모듈을 사용하는 셈이니 성능에서 차이가 날 이유가 없다. 실제 테스트 한 결과를 봐도 톰캣에서 아파치 Native 모듈을 사용하는 것이 순수하게 아파치 Httpd만 사용하는 것과 비교해서 성능이 전혀 떨어지지 않는다.<br/>
따라서 **단지 스태틱 파일 처리의 성능만을 위해서라면 굳이 톰캣 앞에 Apache Httpd를 두는 것은 불필요 하다. 오히려 메모리만 많이 먹고 관리부담은 커지고, 불필요한 부하만 걸릴 뿐이다.<br/>
물론 Httpd의 다른 기능이나 모듈을 사용해야 할 필요가 있다면 그때는 Httpd를 앞에 두고 사용해야겠지만.
예를 들어 하나의 서버에서 PHP애플리케이션과 자바 애플리케이션을 함께 사용하거나, Httpd 서버를 간단한 로드밸런싱을 위해서 사용해야 하는 경우라면 Httpd를 앞에 두고 톰캣을 연결해서 사용하도록 하면 될 것이다.**

[출처]
- [http://sungbine.github.io/tech/post/2015/02/15/tomcat%EA%B3%BC%20apache%EC%9D%98%20%EC%97%B0%EB%8F%99.html](http://sungbine.github.io/tech/post/2015/02/15/tomcat%EA%B3%BC%20apache%EC%9D%98%20%EC%97%B0%EB%8F%99.html)<br/>
- [http://limmmee.tistory.com/4](http://limmmee.tistory.com/4)
