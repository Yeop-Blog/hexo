---
title: input 필드에 숫자만 입력받기
thumbnail: /images/lang_thumbnail.jpg
date: 2017-10-02 15:06:10
categories:
- Language
- HTML
tags:
---
- 출처 : http://webskills.kr/archives/310
~~~html
<!doctype html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>input 필드에 오직 숫자만 입력 받기</title>
</head>
<body>
  <h1>input 필드에 오직 숫자만 입력 받기</h1>
  <form>
    <p><input type="text" onkeydown='return onlyNumber(event)' onkeyup='removeChar(event)' style='ime-mode:disabled;'></p>
  </form>
  <script>
    function onlyNumber(event){
      event = event || window.event;
      var keyID = (event.which) ? event.which : event.keyCode;
      if ( (keyID >= 48 && keyID <= 57) || (keyID >= 96 && keyID <= 105) || keyID == 8 || keyID == 46 || keyID == 37 || keyID == 39 )
        return;
      else
        return false;
    }
    function removeChar(event) {
      event = event || window.event;
      var keyID = (event.which) ? event.which : event.keyCode;
      if ( keyID == 8 || keyID == 46 || keyID == 37 || keyID == 39 )
        return;
      else
        event.target.value = event.target.value.replace(/[^0-9]/g, "");
    }
  </script>
</body>
</html>
~~~
