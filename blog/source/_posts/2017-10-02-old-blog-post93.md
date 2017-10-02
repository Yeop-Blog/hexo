---
title: Java Filter 를 이용하여 XSS (크로스 사이트 스크립트) 를 처리하자
thumbnail: /images/java_thumbnail.jpg
date: 2017-10-02 14:57:17
categories:
- Language
- Java
tags:
---
- 출처 : http://nestofeagle.egloos.com/1809584

업로드한 파일 2가지를 Java파일로 생성 후 아래 소스 코드를 web.xml에 추가
~~~xml
<filter>
  <filter-name>XSS</filter-name>
  <filter-class>xxx.xxxxx.xxx(패키지경로).CrossScriptingFilter</filter-class>
</filter>
<filter-mapping>
  <filter-name>XSS</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
~~~

위에서 ``filter-class``경로는 자신이 만든 ``CrossScriptingFilter.java``패키지 경로 삽입

[Filter 관련 Java 파일 다운로드](https://yeop-blog.github.io/downloads/Filter.zip)
