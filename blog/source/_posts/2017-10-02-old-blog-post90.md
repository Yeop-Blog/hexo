---
title: 모바일 기기 접속시 모바일 페이지로 이동 스크립트
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-10-02 14:38:46
categories:
- Language
- JavaScript
tags:
---
~~~javascript
/**
* 모바일 페이지 강제 이동
*/
//Mobile여부를 구분하기 위함
var uAgent = navigator.userAgent.toLowerCase();
// 아래는 모바일 장치들의 모바일 페이지 접속을위한 스크립트
var mobilePhones = new Array('iphone', 'ipod', 'ipad', 'android', 'blackberry', 'windows ce','nokia', 'webos', 'opera mini', 'sonyericsson', 'opera mobi', 'iemobile');
for (var i = 0; i < mobilePhones.length; i++){
  if (uAgent.indexOf(mobilePhones[i]) != -1){
    location.href="/mobile/home/main.do";
  }
};
~~~
