---
title: sqlplus 에서 자주 쓰는 명령어 모음
thumbnail: /images/oracle_thumbnail.jpg
date: 2017-10-01 17:18:00
categories:
- DB
- Oracle
tags:
---
- 테이블이 어떤것이 있는지 확인할 때
~~~sql
select * from tab;
~~~

- page와 line사이즈 조절 할때
~~~sql
set pagesize 1500;
set linesize 1500;
~~~

- sqlplus를 이용해 오라클XE 포트번호 변경을 하는 방법
 1. SQL Plus 실행 : sqlplus /nolog
 2. Database 접속 : CONNECT SYSTEM/설치할 때 입력한 패스워드
 3. Port 변경 명령 수행 : EXEC DBMS_XDB.SETHTTPPORT(5000);
 4. SQL Plus 종료 : exit
