---
title: 첨부파일 필수값 체크
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-10-02 14:19:54
categories:
- Language
- JavaScript
tags:
---
첨부파일 필수값 체크 관련해서 아래와 같은 스크립트로 체크가 가능하다.  
~~~javascript
forUpdate.validator.set(function() {
 if (typeof $("#uploader-input") === "object" && $("#uploader-input").text() ==="") {
  $.alert({
   message : "<spring:message code="글:X을선택하십시오"></spring:message>".format({0:"<spring:message code="필드:과정:파일"></spring:message>"})
  });
  return false;
 }
 return true;
});
~~~
