---
title: iBatis (followed by either attribute specifications, ">" or "/>".
thumbnail: /images/framework_thumbnail.jpg
date: 2017-10-02 12:08:05
categories:
- Framework
- iBatis
tags:
---
* 출처 : http://blog.daum.net/_blog/BlogTypeView.do?blogid=0MxYQ&articleno=8167305#ajax_history_home

XXXDaoMap.xml:27:39: Element type "result" must be followed by either attribute specifications, ">" or "/>".

뭔가 하고 한참을 들어여 보았더니  
``<result property="kkk" column="KKK"javaType="java.lang.String" jdbcType="CHAR" />``  
에서 ``column="KKK"``와 바로 다음 ``javaType="java.lang.String"``이 바로 붙어 있어서 제대로 읽지를 못해서였다.

``<result property="kkk" column="KKK" javaType="java.lang.String" jdbcType="CHAR" />``
이렇게 해주니 에러는 바로 해결...

지금까지중 가장 어이 없는 에러...
