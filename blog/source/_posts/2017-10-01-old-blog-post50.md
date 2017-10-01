---
title: MySQL order by 튜닝(조금 더 실행속도 부분에 있어서 개선)
thumbnail: /images/mysql_thumbnail.jpg
date: 2017-10-01 17:23:00
categories:
- DB
- MySQL
tags:
---
- 출처 : http://blog.naver.com/PostView.nhn?blogId=parkjy76&logNo=30119980421

MySQL에서ORDER BY를 하면 실행하는데 시간이 많이 걸립니다.  
왜 그럴까라고 생각한적이 있을겁니다.  
저도 ORDER BY에 고민한적이 많습니다.  
이번에ORDER BY에 대한 튜닝방법을 소개하고싶습니다.

그 방법은 서브쿼리를 이용하여 소트가 된 테이블을 결합하여 개선하는 방법입니다.

예를 들어 아래와 같은 SQL문이 있습니다.
~~~sql
SELECT
  t1.col1, t2.col2
FROM
  table1 t1,
  table2 t2
WHERE
  t1.col1=t2.col1 AND t1.col2 = 1
ORDER BY t1.col1 DESC
LIMIT 10;
~~~
이것을 아래처럼 t1을 서브쿼리로 소트해서 결합하는 형태입니다.

~~~sql
SELECT
  t1.col1, t2.col2
FROM
  (SELECT * FROM table1 ORDER BY col1 DESC) t1,
  table2 t2
WHERE
  t1.col1=t2.col1 AND t1.col2 = 1
LIMIT 10;
~~~
이와 같은 튜닝이 유효하기 위해서는 다양한 조건이 있기때문에 항상 효과가 있다고는 말할수 없습니다만  
제가 테스트한 쿼리에서는 using filesort가 없어져 꽤 효과가 있었습니다.  
효과의 정도가 크다고는 말할수 없지만 수백배였습니다.(진짜?)

이글을 읽고 느낀점은 mysql의 플래너는 역시 머리가 나쁘다이다.  
물론 인덱스를 정상적으로 설정했다는 가정에서 말하는거지만 버전에 따라 다를수도 있지만

postgresql에 비해 역시 플래너가 -\_-
