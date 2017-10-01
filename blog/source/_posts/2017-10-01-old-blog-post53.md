---
title: INNER JOIN시 값이 여러개 나와서 문제일 경우 EXISTS 이용하자.
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-01 17:37:00
categories:
- Tip's
tags:
---
예를 들어..
~~~sql
select * from A a
inner join B b
...
~~~
일 경우 같은 데이터의 값이 여러개 나와서 문제가 된다면..
~~~sql
select * from A a
and exists (select 1 from B b);
~~~
이런식으로 해결을 하면 된다.
