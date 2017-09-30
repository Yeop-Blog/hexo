---
title: 브라우저 창 닫기 소스
thumbnail: /images/tip_thumbnail.jpg
date: 2017-09-30 18:17:00
categories:
- Programming
- Tip's
tags:
---
팝업창이 아닌 일반 브라우저에서 브라우저를  
widows.close() 혹은 self.close()를 사용해서 닫으면  
"지금 보고 있는 웹 페이지에서 창을 닫으려고 합니다.  
이 창을 닫으시겠습니까?"  
이라는 문구의 Confirm 창이 뜹니다.  
Confirm 창이 안생기게 하려면 아래처럼 하시면 됩니다.  
```html
<a href="#" onclick="top.window.opener = top; top.window.open('','_parent', ''); top.window.close();">창닫기(경고창 없음)</a>
```
