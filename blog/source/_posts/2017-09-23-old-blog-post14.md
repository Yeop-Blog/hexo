---
title: 5장. 동적 웹 페이지(HTML 요소, DOM에 관해)
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-23 21:13:32
categories:
- Language
- JavaScript
tags:
---
1. 컨텐츠나 HTML을 수정하려면 크게 2가지 과정을 거쳐야 한다.
 - 페이지의 HTML 요소를 얻어야 한다.
 - HTML 요소로 무엇인가를 합니다. 여기서 무엇인가는 클래스 속성 추가/제거, HTML 요소 속성 변경, 새 컨텐츠 추가, HTML 요소 제거, HTML 요소에서 정보 추출 등이 있다.

2. 문서 객체 모델(DOM)  
**DOM은 Document Object Model의 약자이다.**
DOM은 자바스크립트가 웹 페이지에 있는 **HTML 요소와 통신하기 위해서 필요한 정보를 제공**한다.  
웹 브라우저는 태그(tag), 속성(attribute), 텍스트(node)의 조직화된 집합체로 구성되어 있다고 볼 수 있다.

3. HTML 요소 선택
 - **getElementById()**  
 : 고유한 id를 가진 단일 노드를 찾을 때 쓰는 메소드.
 ```javascript
 document.getElementById('header');
 // 해당하는 페이지에서 'header'라는 id가 들어간 태그를 찾아라.

 OR

 var looker = 'body';
 var foundNode = document.getElementById(looker);
 // 'body'라는 id가 들어간 태그를 찾아라
 ```
 - **getElementsByTagName()**  
 : 여러개의 HTML 요소를 찾아야 할 때 쓰는 메소드.
 ```javascript
 var pageLinks = document.getElementsByTagName('a');
 // 이 페이지에서 <a> 태그를 찾아 pageLinks에 저장하라.
 ```
 - **innerHTML**  
 : 특정 노드 내부의 코드 검색 또는 노드 내부의 컨텐츠를 바꾸는것도 가능.
 ```javascript
 var headLine = document.getElementsById('header');
 headLine.innerHTML = '원하는 HTML을 입력합니다.';
 // 'header'라는 id를 가진 HTML 요소 컨텐츠는 '원하는 HTML을 입력합니다.'로 바뀐다.
 ```
4. DOM의 문제  
브라우저 종류에 따라 각기 다르게 해석하는 부분이 있기 때문에 이런 부분에 있어서 생각을 해볼 필요는 있다.
