---
title: Tomcat SSL 적용하기
thumbnail: /images/server_thumbnail.jpg
date: 2017-10-01 17:29:00
categories:
- Server
- Apache/Tomcat
tags:
---
- 출처 : http://devhome.tistory.com/64

#### TOMCAT SSL 적용

JDK에 포함된 keytool을 이용하여 Tomcat에 SSL을 적용하는 방법을 소개한다.

1. **JDK bin 폴더라 이동한다.**  
\- %JAVA_HOME%\bin  
Ex) Win7의 경우 'C:\Program Files (x86)\Java\jdk1.6.0_32\bin' 경로에 존재한다. (버전에 따라 상이하다)
<br>
2. **JDK를 이용해 Tomcat 인증서를 생성한다.**  
\- keytool -genkey -alias tomcat -keyalg RSA  
{% img /images/post_images/old-blog-post52-1.png 첫번째 이미지 %}
<br>
3. **생성된 .keystore 파일 확인**  
\- 사용자 홈 폴더에 .keystore 파일이 생성되어 있음  
\- Ex) Win7의 경우 'C:\Users\사용자계정\.keystore' 위치에 생성되어 있음
<br>
4. **Tomcat server.xml 설정**
~~~
<connector sslprotocol="TLS" clientauth="false" keystorepass="passwd"
keystorefile="${user.home}/.keystore" secure="true" scheme="https" maxthreads="150"
sslenabled="true" protocol="HTTP/1.1" port="8443"></connector>
~~~
<br>
5. **Tomcat 시작 및 SSL 적용확인**  
\- https로 개발된 페이지를 접근해 보면됨  
\- Ex) https://localhost:8443
