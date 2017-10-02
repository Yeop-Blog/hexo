---
title: 윈도우서비스 제거 및 생성 방법
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 10:12:55
categories:
- Tip's
tags:
---
- 출처 : http://blog.naver.com/kodoi486?Redirect=Log&logNo=70025256677

대부분은 경우를 보면 윈도우 서비스를 추가하거나 제거하는 방법을 잘 몰라서 그냥 방치를 하거나 불필요한 서비스인 경우는 중지만 해놓고 있는 경우가 많다.

인터넷에서 윈도우 서비스를 관리 할 수 있는 유틸리티를 받아서 관리를 하는 분도 있기도 하지만 만약 해킹으로 인하여 인터넷이 불가능한 상황이라면 인터넷에서 이런 유틸리티를 받을수도 없다.

하지만 Windows Control (이하 SC)를 이용하면 윈도우 서비스를 쉽게 생성 할수도 있고, 사용하지 않는 서비스는 삭제 할 수있다.
{% img img leftimg /images/post_images/old-blog-post67-1.jpg 첫번째 이미지 %}

사용법도 무지 간단하다

**서비스를 삭제를 하고자 하는 경우에는 아래와 같이 입력하면 된다.**

sc delete 서비스명  
ex) ``sc delete msdtc``

**서비스에 대한 정보를 보고자 할 경우에는 아래와 같이 입력하면 된다.**

sc query 서비스명  
ex) ``sc query msdtc``

**서비스 Start Stop은 아래와 같다**

sc start 서비스명  
ex) ``sc start abel``

sc stop 서비스명  
ex) ``sc stop abel``

**서비스 설정을 바꾸고자 할때에는 config를 입력하면 된다.(그림 참고)**  
{% img img leftimg /images/post_images/old-blog-post67-2.jpg 두번째 이미지 %}

**윈도우 서비스를 생성하고자 하는 경우에는 추가적으로 실행해주는 옵션이 많은데, 친절하게 옵션 설명이 나오므로 참고 하면 되겠다.**  
{% img img leftimg /images/post_images/old-blog-post67-3.jpg 세번째 이미지 %}
