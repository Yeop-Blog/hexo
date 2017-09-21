---
title: 3장. 프로그램에 로직과 제어 추가
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-22 00:01:01
categories:
- Language
- JavaScript
tags:
---
1. 자바스크립트에는 조건문을 추가하여 아래와 같은 명령을 수행할 수 있다.
 - **폼 유효성 검사**
 - **드래그 앤 드롭**
 - **입력값 검증**

2. if문의 사용법은 아래와 같이 다양하게 쓸 수 있다.
 - ``if(조건) { }``  
 - ``if(조건) { } else { }``  
 - ``if(조건) { } else if(조건) { } else { }``  
 - 조건에는 AND연산자(&&)와 OR(||)연산자, 조건 부정(!)등이 들어갈 수 있다.

3. **루프를 이용하여 반복 작업** 을 할 수도 있다.  
``while(조건) { }``  
``do { } while(조건);``

4. 함수 : 유용한 코드를 재사용 가능한 명령으로 바꾸기  
함수의 기본 구조는 아래와 같다.  
```javascript
function functionName() {
      //실행할 자바스크립트 코드
}
//Example
function printToday( {
      var today = new Date();
      document.write(today.toDateString());
}
```  
실행을 하려면 ``printToday();``

5. 함수에 정보를 건네줄 때는 **파라미터(parameter)**를 이용하면 된다.  
기본 구조는 아래와 같다.
```javascript
function functionName(parameter) {
      //실행할 자바스크립트 코드
}
//Example
function print(message) {
      document.write(message);
}
```
실행을 하려면 ``print('Hello World!');``  
파라미터 값은 여러개 추가가 가능하다.
```javascript
function functionName(parameter1, parameter2, parameter3) { }
```

6. 함수에서 정보를 가져 올때는 return을 이용하면 된다.
```javascript
function functionName(parameter) {
      //실행할 자바스크립트 코드
      return value;
}
//Example
var TAX = 80;
function calculateTotal(quantity, price) {
      var total = quantity * price * (1+TAX);
      var formattedTotal = total.toFixed(2);
      return formattedTotal;
}
var saleTotal = calculateTotal(2, 16);
document.write('Total cost is : $' + saleTotal);
```
