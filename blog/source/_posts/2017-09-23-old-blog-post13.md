---
title: 4장. 문자, 숫자, 날짜 다루기
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-23 21:00:23
categories:
- Language
- JavaScript
tags:
---
1. 문자열의 대,소문자 바꾸는 메소드
 - 문자열을 **소문자에서 대문자**로 바꾸고 싶은 경우 : **.toUpperCase();**
 - 문자열을 **대문자에서 소문자**로 바꾸고 싶은 경우 : **.toLowerCase();**  
 ```javascript
 answer.toLowerCase();
 ```

2. **문자열을 검색**하고 싶은 경우 **.indexOf('찾는 문자열')** 메소드를 사용한다.  
```javascript
 browser.indexOf('MSIE');
```

3. **문자열의 일부**를 떼어내려면 **slice()** 메소드를 사용한다.  
```javascript
 var url = 'http://www.sawmac.com';
url.slice(7); ==== 실행후 ====> www.sawmac.com
```

4. **문자열의 패턴**을 찾으려면 **정규표현식(regular expression)**을 알아야 한다.  
< 자바스크립트 책 P150 ~ 168까지 참고할것 >

5. **문자열을 숫자로 변환**하는 방법에는 다음과 같은 방법이 있다.  
 - **Number()** : 전달된 문자열을 숫자로 변환
 ```javascript
 var a = '3';
 var b = '4';
 var total = Number(a) + Number(b); // 7
 ```

 - **parseInt()** : 텍스트를 포함하고 있으면 그 부분은 제외하고 숫자로 변환  
 ```javascript
 var age = '20살';
 age = parseInt(age, 10); // 20
 //여기서 age 콤마 뒤에 10은 10진수로 변환한다는 것을 의미한다.
 ```

 - **parseFloat()** : parseInt()와 비슷하지만, 소수점을 포함한 문자열에 사용할 수 있다  
 ```javascript
 var space = '4.5제곱미터';
 space = parseFloat(space); // 4.5
 ```

6. **숫자인지 확인**을 하려면 전에 앞서 언급했던 **isNaN()** 메소드를 사용한다.
```javascript
var x = '10';
if(isNaN(x)){
      //숫자가 아닐 때
} else {
      //숫자일 때
}
```

7. **반올림**을 해야 하는 경우에는 **round()** 메소드를 사용한다.
```javascript
var num = 10.25;
var roundNum = Math.round(num); // 10
```

8. **올림**을 해야 하는 경우에는 **ceil()**, **내림**을 해야 하는 경우에는 **floor()** 메소드를 사용한다.

9. **소수점 자리 고정**을 해야 할 경우 **toFixed()** 메소드를 사용한다. (숫자에만 사용 가능)
```javascript
var avg = 82;
var printAvg = avg.toFixed(2); // 82.00
var avg2 = 81.289;
var printAvg2 = avg2.toFixed(2); // 81.29 (지정한 자리수보다 많으면 반올림 되서 나온다)
```

10. **무작위 숫자**를 만들려면 **Math.random()** 메소드를 사용한다.

11. **현재 날짜와 시간**을 구할때는 **Date 객체**를 사용한다. Data 객체를 생성후 관련 메소드를 사용할 수 있다.
```javascript
var now = new Date();
var year = now.getFullYear();
```
 - 년도 : getFullYear() -> 2012년
 - 월 : getMonth() -> 월은 0이 1월 11이 12월을 의미한다.
 - 일 : getDate() -> 1부터 31일까지
 - 요일 : getDay() -> 요일은 0이 일요일, 6이 토요일을 의미한다.
 - 시간 : getHours() -> 0부터 23까지의 숫자로 기존 24시 체계와 동일하다.
 - 분 : getMinutes() -> 0부터 59분까지
 - 초 : getSeconds() -> 0부터 59초까지
 - getTimes() -> 1970년 1월 1일 0시부터 초단위로 계산한 시간을 나타냄
