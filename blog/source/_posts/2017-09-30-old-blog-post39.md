---
title: 영문 숫자 조합 스크립트(비밀번호 영문+숫자 조합 체크할경우)
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-30 21:23:00
categories:
- Language
- JavaScript
tags:
---
- 출처 : http://bausluv.blog.me/60146430648

ASP 에서 정규식으로 체크 하려다가 예외의 경우가 있길래 스크립트 함수로 만들어 체크 하는걸 정규식으로 만들어보았습니다.  
~~~javascript
// 비밀번호 조합
function CheckPass(str){
   var reg1 = /^[a-z0-9]{7,14}$/;    // a-z 0-9 중에 7자리 부터 14자리만 허용 한다는 뜻이구요
   var reg2 = /[a-z]/g;    
   var reg3 = /[0-9]/g;
   return(reg1.test(str) &&  reg2.test(str) && reg3.test(str));
};
~~~
정규식을 이용하여 각 패턴별로 true or false 를 반환 합니다.

함수 넣으시고 체크 하실때는 폼체크 하시면서~
~~~javascript
if(CheckPass(form.passwd.value) == false){
  alert("비밀번호는 영문 숫자 조합 7자리 이상입니다.");   // 넣고 싶은 메세지 넣으시면 됩니다~
  return;
}
~~~
