---
title: 5장. 동적 웹 페이지(자바스크립트 라이브러리)
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-23 21:29:00
categories:
- Language
- JavaScript
tags:
---
1. 다양한 라이브러리가 있지만 여기서 소개하는 것은 **jQuery라이브러리**를 사용한다.
 - jQuery라이브러리 외에도 YUI(Yahoo User Interface), Prototype, Dojo Toolkit, Mootools 등이 있다.

2. jQuery의 장점  
 - 상대적으로 **작은 파일 크기**
 - 웹 디자이너에게 친숙함
 - 신뢰성
 - **무료**
 - **개발자 커뮤니티가 활성화** 되어 있다는 점
 - **플러그인**

3. jQuery 파일은 3가지 종류가 있다.
 - Uncompressed(압축안함)
 - Packed(압축)
 - **Minified(최소화)**
  1) 보통은 Minifed 버전의 jQuery 파일을 다운 받아 쓰는것이 좋다.
  2) 사용하는 방법은 ``<script type="text/javascript" src="js/jquery.js"></script>`` 이런식으로 선언하고 사용하면 된다.

4. HTML 요소 선택
 - jQuery의 기본적인 문법은 아래와 같다.  
 ```javascript
 $('selector')
 ```
 - 예를 들어 banner라는 id를 가진 태그를 선택 하려면 아래와 같다.
 ```javascript
 $('#banner')
 ```
 - 태그 내 속성을 아래와 같이 변경을 할 수 있다.
 ```javascript
 $('#banner').html('<h1>제목 크기를 변경하였습니다.</h1>');
 jQuery('#banner').html('<h1>제목 크기를 변경하였습니다.</h1>');
 ```
 - 기존의 DOM방식과 jQuery방식의 차이를 아래 예제를 통해 보면 쉽게 알 수 있다.  
  1) DOM 방식 : ``var result = document.getElementById('message');``
  2) jQuery 방식 : ``var result = $('#message');``
 - HTML 요소 선택도 차이점을 보여준다.
  1) DOM 방식 : ``var linksList = document.getElementsByTagName('a');``
  2) jQuery 방식 : ``var linksList = $('a');``
 - 클래스를 선택할때는 다음과 같이 하면 된다.
 ```javascript
 $('.submenu')
 ```

5. 고급 선택자
 - 하위 선택자
 ```javascript
 $('#navBar a')
 ```
 - 자식 선택자
 ```javascript
 $('body > p') // 여기서 <body>태그보단 안에 <p>태그가 속해 있는 경우
 ```
 - 인접 형제 선택자
 ```javascript
 $('h2 + div') // 실제로 써 봐야 알듯..?
 ```
 - 속성 선택자
 ```javascript
 $('img[ alt]') // alt 속성이 있는 <img>태그를 찾는 경우
 ```
 - 속성=값
 ```javascript
 $('input[ type=text]') // 텍스트 박스만 선택하고 싶은 경우
 ```
 - 속성^=값
 ```javascript
 $('a[ href^=http://]') // 외부 사이트 링크를 찾고 싶은 경우
 ```
 - 속성$=값
 ```javascript
 $('a[ href$=.pdf]') // pdf파일을 가르키는 링크를 찾고 싶은 경우
 ```
 - 속성*=값
 ```javascript
 $('a[ href*=daum.net]') // daum.net을 가르키는 모든 링크를 찾고 싶은 경우
 ```

6. jQuery 필터(이후 부터는 각 메소드들의 사용법 및 설명만 참고함)
 - :even / :odd  
 : 특정 그룹에서 짝수 또는 홀수 번째의 HTML 요소 선택
 ```javascript
 $('tr:even')
 ```
 - :not()  
 : 특정 선택자에 해당하지 않는 HTML 요소 선택
 ```javascript
 $('a:not(.navButton)'); // navButton 클래스가 없는 모든 <a> 태그 선택
 ```
 - :has()  
 : 또 다른 선택자를 가진 HTML 요소 선택
 ```javascript
 $('li:has(a)') // <a> 태그 내부에 포함된 <li> 태그를 찾을때
 ```
 - :contains()  
 : 특정 텍스트를 포함하고 있는 HTML 요소 선택
 ```javascript
 $('a:contains(클릭하세요!)') // 클릭하세요! 라는 텍스트가 있는 링크를 찾을때
 ```
 - :hidden  
 : 숨겨진 HTML 요소를 선택
 ```javascript
 $('div:hidden').show();
 ```
 - :visible  
 : hidden과는 반대로 화면상에서 보이는 HTML 요소를 선택
