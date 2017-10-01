---
title: MSSQL ALTER 명령어
thumbnail: /images/mssql_thumbnail.jpg
date: 2017-10-01 18:11:00
categories:
- DB
- MSSQL
tags:
---
- 출처 : http://blog.naver.com/soo02da/150094175853


1. 테이블 필드 수정하기  
alter table [테이블명] alter column [칼럼명] [형식] [기타 제약 조건];  
~~~sql
alter table user_mstr alter column user_nm varchar(200) not null;
~~~

2. 필드 삭제 하기  
alter table [테이블명] drop column [칼럼명];

3. 필드 추가하기  
alter table [테이블명] add [칼럼명] [형식] [기타 제약 조건];  
~~~sql
alter table user_mstr add user_pw_old varchar(100) not null;
~~~

4. 필드 이름수정  
sp_rename '테이블명.[칼럼명]', 바뀔칼럼명', 'COLUMN'  
~~~sql
sp_rename 'bbs_article.[thumb]', 'thumb_nm', 'COLUMN'
~~~
