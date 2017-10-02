---
title: 테이블 td에서 글이 늘어났을때 자동으로 줄바꿈 하게끔
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 13:37:41
categories:
- Tip's
tags:
---
- 출처 : http://cafe.naver.com/domfam/1172

``style="word-break:break-all;"``  
아 저거 오늘 완전 유용한 소스네요~

테이블 width 값을 모두 줬음에도 불구하는 저 늘어나는 테이블때문에 어찌할바를 몰라 쩔쩔매며 div를 사용해서 해보기도 하고 별의별 방법을 찾던중 윌리님 덕분에 오늘 유용한 소스 하나 얻어가네요.

저렇게 영문을 td안에 넣었을 경우 주체할수 없이 늘어나는 저 테이블..

그럴땐 고민고민하지 마시고  
``<td style="word-break:break-all;">``이걸 넣어주세요~  
그러면 정해준 width값을 벗어나지 않는답니다.
