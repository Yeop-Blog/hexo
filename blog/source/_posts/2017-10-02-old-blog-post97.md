---
title: window.onload 대신 사용 가능한 jQuery, javascript 함수
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-10-02 15:12:07
categories:
- Language
- JavaScript
tags:
---
window.onload의 기본 사용법은 아래와 같음
~~~javascript
window.onload = function () {
   alert('test');
}
~~~
jQuery를 사용하는 경우 아래와 같음
~~~javascript
$(document).ready(function() {
   alert('test');
});
~~~
위 2가지 방법으로도 안되는 경우 아래와 같은 함수를 사용해 볼 것
~~~javascript
function window::onload(){
   alert('test');
}
~~~
