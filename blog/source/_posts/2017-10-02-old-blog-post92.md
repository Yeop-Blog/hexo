---
title: Http Method (GET, POST, HEAD, PUT, DELETE, TRACE) 제한하기
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 14:46:57
categories:
- Tip's
tags:
---
- 출처 : http://jedagi.tistory.com/90

보안때문에 GET, POST, HEAD 정도만 사용하고 PUT, DELETE, TRACE는 막아두는데 방법은 WEB-INF\web.xml에 코드 추가
~~~xml
<security-constraint>
  <display-name>openCoss http Auth</display-name>
  <web-resource-collection>
  <web-resource-name>SecureFile</web-resource-name>
  <url-pattern>/*</url-pattern>
  <!--
  <http-method>GET</http-method>
  <http-method>POST</http-method>
  -->
  <http-method>HEAD</http-method>
  <http-method>PUT</http-method>
  <http-method>DELETE</http-method>
  <http-method>TRACE</http-method>
  </web-resource-collection><auth-constraint>
  <role-name>openCmsAuth</role-name>
  </auth-constraint>
</security-constraint>
~~~

확인 하는 어플은 간단게 만들었다...  
[httpMethodCheck 다운로드](https://yeop-blog.github.io/downloads/httpMethodCheck.zip)
