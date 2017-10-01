---
title: Oracle SQL 제약조건 삭제방법
thumbnail: /images/oracle_thumbnail.jpg
date: 2017-10-01 21:35:00
categories:
- DB
- Oracle
tags:
---
``alter table member drop column id cascade constraints``  
그리고 이어서  
``drop table member``

- MEMBER
~~~sql
alter table member drop column id cascade constraints;
drop table member;
~~~

- BBS
~~~sql
alter table bbs drop column no cascade constraints;
drop table bbs;
~~~

- BBS_COMMENT
~~~sql
drop table bbs_comment;
~~~

- 휴지통 비우기  
``purge recyclebin;``
