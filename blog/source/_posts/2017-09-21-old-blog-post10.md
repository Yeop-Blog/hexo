---
title: 1장. JavaScript 기초 부분
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-21 23:26:34
categories:
- Language
- JavaScript
tags:
---
1. 기본 JavaScript 형식은 아래와 같다.
```javascript
<script type="text/javascript">
..
</script>
```
2. 외부 자바스크립트 파일(.js)을 이용해서 자바스크립트 코드를 링크할 수 있다.
```javascript
<script type="text/javascript" src="navigation.js"></script>
```
3. 경고창을 띄우려면 아래와 같은 메소드를 사용한다.
```javascript
<script type="text/javascript">
      alert('hello world');
</script>
```
4. 스크립트 오류에는 아래와 같은 경우를 주의해서 살펴보는것이 좋다.  
\- 인수 목록 뒤에 닫는 괄호 ')'를 빼먹는 경우  
 ex) ``alert('hello'``  
\- 종료되지 않은 문자열  
ex) ``alert(hello)``  
\- 복합문에서 }를 빼먹는 경우  
ex) ``{ ... }``  
\- XXX가 정의되지 않았습니다.  
ex) ``aler('hello')``  
\- 문법상 실수
