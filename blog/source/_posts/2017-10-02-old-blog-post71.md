---
title: iframe 관련 '사용 권한이 없습니다' 라는 오류가 있을시
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 11:50:17
categories:
- Tip's
tags:
---
iframe에서 append가 되지 않는 부분이 있어서 div로 처리를 하면 에러가 해결이 된다.  
아래 예를 보고 차후 다시 한번 이 부분에 대한 공부가 필요.  
- Javascript 부분
~~~javascript
forViewCount = $.action("ajax");
forViewCount.config.formId      = "FormViewCount";
forViewCount.config.type        = "html";
forViewCount.config.containerId = "blankArea";  //여기가 포인트 부분!!
forViewCount.config.url         = "<c:url value="/library/update/viewCount/ajax.do"/>";
forViewCount.config.fn.complete = function() {
  forDownload.run();
};
~~~
- HTML 부분
~~~html
<div id="blankArea" style="display: none;"></div> //ID값을 맞춰줄것!!
~~~
