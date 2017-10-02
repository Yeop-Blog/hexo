---
title: 사용자정의 태그에 관한 예제
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-01 16:57:00
categories:
- Tip's
tags:
---
- 출처 : http://blog.naver.com/judge41?Redirect=Log&logNo=140105480130

JSTL로 하려고 했는데, 일단 이거 먼저 ㅎ

접두어 : extag  
태그 : copyright  
출력 내용 : 취업하게 해주세요...제발...  
TLD 파일 : TestTag.tld  
태그 핸들러 클래스 : TestTagHandler.java  
태그 지시어 사용 : exam.jsp  

[TestTagHandler.java]  
태그 핸들러 클래스는 태그의 실제 기능을 가진 자바 클래스 파일이다.

~~~java
package taglib;

import java.io.*;
import javax.servlet.jsp.*;
import javax.servlet.jsp.tagext.*;

//TagSupport 클래스를 상속받아 Handler 클래스를 만든다.
public class TestTagHandler extends TagSupport {

  //doStartTag() 를 오버라이딩한 메서드로 JSP에서 시작 태그를 만날 때 호출된다.
  public int doStartTag() throws JspException {
    try {
      //pageContext로 모든 내장객체를 가져올 수 있다.
      JspWriter out = pageContext.getOut();
      out.println("취업하게 해주세요...제발...");
    } catch(IOException e) {
      e.printStackTrace();
    }

    //태그에 본문이 없는 경우기 때문에 SKIP_BODY를 리턴한다.
    return SKIP_BODY;
  }
}
~~~

[TestTag.tld]  
이클립스를 사용하여 개발할 때 new메뉴를 통해 tld파일을 만들고자 한다면 결코 찾을 수 없을 것이다. 밑에서 설명할께...

~~~
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE taglib PUBLIC "-//Sun Microsystems, Inc.//DTD JSP Tag Library 1.2//EN"
"http://java.sun.com/dtd/web-jsptaglibrary_1_2.dtd" >

<taglib>
<tlib-version>1.2</tlib-version>
<jsp-version>1.2</jsp-version>
<short-name>jspbook</short-name>

<tag>
<name>copyright</name>
<tag-class>taglib.TestTagHandler</tag-class>
<body-content>empty</body-content>
</tag>

</taglib>
~~~

[exam.jsp]  
``<extag:copyright/>``이 부분을 작성할 때 반드시 붙여써야 한다.<br> ``<extag : copyright/>``이런 식으로 띄워쓰면 화면에 결과가 나타나지 않는다.  
(콜론 사이를 항상 띄워쓰는 버릇이 있어 처음에는 결과가 안나오더라...버릇이 무서워 ㄷㄷ)  
~~~
<%@ page contentType="text/html; charset=EUC-KR"%>
<%@ taglib uri="WEB-INF/tld/TestTag.tld"  prefix="extag"%>
<html>
  <head>
    <title>사용자 정의 태그</title>
  </head>
  <body>
    <center><br>
    <h2><extag:copyright/></h2>
    </center>
  </body>
</html>
~~~
---
결과화면  
{% img /images/post_images/old-blog-post47-1.jpg 첫번째 이미지 %}
