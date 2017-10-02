---
title: Javascript text input창에서 엔터 검사->엔터입력시 스크립트 호출
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-10-02 14:05:07
categories:
- Language
- JavaScript
tags:
---
- 출처 : http://blog.naver.com/pero80/100063216873
~~~html
<input name="kw" type="text"  onkeypress="javascript : if (event.keyCode == 13) key();">
~~~
