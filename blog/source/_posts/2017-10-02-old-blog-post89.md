---
title: 텍스트 범위 벗어나면 숨기고 ... 붙이기
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 14:33:55
categories:
- Tip's
tags:
---
- 출처 : http://saybox.tistory.com/70
~~~html
<div style="width:100;text-overflow:ellipsis;overflow:hidden">abcdefghight1234567890</div>
~~~
**결과** : abcdefghig...  
IE 6.0 이상에서 적용되며 div 에서 사용시 폭을 벗어난 글자는 숨기고 "..." 처리 해줌.  
굿이 일일이 php 에서 길이계산후 "..." 처리 안해도 손쉽게 적용 가능
