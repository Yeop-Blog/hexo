---
title: The content of elements must consist of well-formed character data or markup
thumbnail: /images/framework_thumbnail.jpg
date: 2017-10-01 17:47:00
categories:
- Framework
- iBatis
tags:
---
iBatis 는 XML 형식이기 때문에 부등호가 들어간 쿼리를 사용할때 에러가 발생한다.  
The content of elements must consist of well-formed character data or markup.  
이럴때에는 부등호가 들어간 쿼리를 **<![CDATA[ 쿼리 ]]>** 로 감싸줘야 한다.
~~~sql
select
  ROWNUM, no2, writer2, title2,
  regdate2, hit2, contents2, upfile2,
  password2, recommend2, category2
from
  (select
      ROWNUM, no2, writer2, title2, to_char(regdate2,'yyyy-mm-dd') as regdate2,
      hit2, contents2, upfile2, password2, recommend2, category2
   from twice_board
   order by hit2 DESC
  )
where <![CDATA[ROWNUM<=3]]>
~~~
