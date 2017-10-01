---
title: Ctrl+C,Ctrl+V, F5 복사방지 스크립트
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-01 18:00:00
categories:
- Tip's
tags:
---
#### IE, Chrome에서 사용 가능

- 키보드
~~~javascript
textbox_KeyDown = function () {
 if(event.keyCode == 86 && event.ctrlKey) {
  event.keyCode = 0;
  event.cancelBubble = true;
  $.alert({message : "
"});
  window.event.returnValue = false;
 }else if(event.keyCode == 67 && event.ctrlKey){
  event.keyCode = 0;
  event.cancelBubble = true;
  $.alert({message : ""});
  window.event.returnValue = false;
 }
};
~~~

#### FF에서 사용 가능
- FF에서 Ctrl키값 방지
~~~javascript
$(function(){
 $("input:text").keydown(function(evt){
  if(evt.keyCode==17){
   evt.keyCode = 0;
   evt.cancelBubble = true;
  }
 });
});
~~~

#### IE, Chrome, FF에서 사용 가능
- 마우스 우클릭 방지
~~~javascript
clickIE = function(){
 if (document.all) {
  return false;  
 }
};
clickNS = function(e){
 if (document.layers || (document.getElementById && !document.all)) {
  if (e.which==2 || e.which==3) {   
   return false;   
  }
 }
};
//layer로 감싼 경우는 if문이 들어간다. layer가 아닌 경우 if문 제외하고 captureEvents도 삭제한후 사용.
if (document.layers) {
 document.captureEvents(Event.MOUSEDOWN);
 document.onmousedown=clickNS;
}else{
        document.onmouseup=clickNS;
 document.oncontextmenu=clickIE;
}
document.oncontextmenu=new Function("return false");
또는
document.onmousedown=clickNS;
document.onmouseup=clickNS;
document.oncontextmenu=clickIE;
document.oncontextmenu=new Function("return false");
~~~

- 키보드 방지
~~~javascript
function LockF5(e){   
    var key = (e) ? e.keyCode : event.keyCode;
   if(key==8 || key==116 || key==78 || key==82){
      if(e){   //표준
         e.preventDefault();
      }
      else{ //익스용
         event.keyCode = 0;
         event.returnValue = false;
      }
   }
}
document.onkeydown = LockF5;
~~~
