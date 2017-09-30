---
title: 브라우저 "닫기" 버튼 만들기 (window.close, self.close 관련)
thumbnail: /images/tip_thumbnail.jpg
date: 2017-09-30 21:34:00
categories:
- Tip's
tags:
---
- 출처 : http://happyjung.com/gnuboard/bbs/board.php?bo_table=lecture&wr_id=608&sca=JavaScript

홈페이지에서 공지사항이나 이벤트와 같은 창이 열리고, 그 창에서 "닫기" 버튼을 클릭하면 창이 사라지는 기능입니다.

1. History 활용  
정상 : IE 11  
작동안함 : FireFox 36.0, Chrome 4.0.22  
~~~html
<script type="text/javascript">
<!--
function closeWin() {
var nvua = navigator.userAgent;
if (nvua.indexOf('MSIE') >= 0){
if(nvua.indexOf('MSIE 5.0') == -1) {
top.opener = '';
}
} else if (nvua.indexOf('Gecko') >= 0){
top.name = 'CLOSE_WINDOW';
wid = window.open('','CLOSE_WINDOW');
}
top.close();
}
// -->
</script>
<a href="#" onclick="javascript:history.onclick=closeWin();">닫기</a>
~~~

2. A링크 활용  
정상 : IE 11, FireFox 37.0.2, Chrome 42.0.23
~~~html
<a href="#" onclick="javascript:window.close()">창닫기</a>
<a href="#" onclick="javascript:self.close();">닫기</a>
~~~

3. 버튼 클릭으로 창 닫기  
정상 : IE 11  
작동안함 : FireFox 36.0, Chrome 42.0.232  
~~~html
<input type="button" value="창닫기" onClick="window.close()">
<input type="button" value="창닫기" onClick="window.open('','_self').close();">
~~~

4. 프레임셋 문서를 이미지클릭으로 닫기
~~~html
<a href="#" onclick="javascript:top.window.close()"><img border="0" src="../close.gif"></a>
~~~

5. 프레임셋 문서 전체닫기
~~~html
<a href="javascript:top.window.close()">창닫기</a>
~~~

6. 프레임셋 문서를 버튼클릭으로 닫기
~~~html
<input type="button" value="창닫기" onclick="top.window.close()">
~~~

7. 부모창 닫기
~~~html
<a href="#" onclick="javascript:parent.close();">닫기</a>
~~~

< 참고자료 >  
http://www.ddalchi.co.kr/ddart/cgi-bin/ddbread.cgi?db=bbs_06&anum=39&page=1  
http://www.dbinfo.co.kr/bbs/board.php?bo_table=dbinfo_html_javascri&wr_id=31  
http://luvbaby.tistory.com/96
