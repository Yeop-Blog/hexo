---
title: MSSQL 간단하게 테이블 백업, 복구하기
thumbnail: /images/mssql_thumbnail.jpg
date: 2017-10-01 18:14:00
categories:
- DB
- MSSQL
tags:
---
- 출처 : http://jajking.tistory.com/5

#### 백업
회사에서 중요한 데이터 베이스 작업을 앞두고 긴장하는 경우가 많은데요  
이럴때는 간단하게 필요한 정보만 백업 해 두고싶은욕구가 생기죠..  
바로 이런 경우에 요긴하게 쓰일 수 있는 게 바로  

<span style='color: #5c7fb0; font-weight:bold;'>SELECT INTO 구문입니다.</span>

select into 구문은  create table 와 insert ~ select 구문을  
합쳐 놓은거 라고 생각하지면 되겠습니다.

예로 회사 상용디비에 업뎃을 걸거나 삭제를 날려야 할때 예상치 못한 결과를 대비해서  
미리 테이블 자체를 백업을 하는것이 가능합니다.  
(저는 간떨려서 꼭 해 둡니다...ㅋㅋㅋ)

<span style='color: #801fbf; font-weight:bold;'>USE 사용할 데이터베이스  
SELECT * INTO newtable FROM oldtable</span>

이렇게 해두면 상당한 크기의 테이블이라도 단 몇초만에 백업가능합니다.  
(한 레코드  100byte 정도의 100만건이라도 1분을 안 넘깁니다.)

하지만 주의점은 어디까지나 임시 백업용이라는점을 잊지마세요.  
테이블의 데이터만 완전 백업을 받을 수 있는거지, **기존 테이블에 걸려있는  
각종 키정보나 제약 정보는 아무것도 따라오는것이 아니랍니다.**

중요 업뎃 날리실때 꼭 테이블 백업 하시고 가벼운 맘으로 where 구문없이 ..ㅋㅋ (농담요.ㅋ)

대한민국 개발자 여러분 홧팅하세요..^^

참고로 MSSQL 기준으로 작성된 글 입니다.  
아마도 oracle 에서는 ``CREATE TABLE newtable AS SELECT * FROM oldtable`` 이라는 구문을 사용하실수 있을겁니다.

#### 복구
~~~sql
SET IDENTITY_INSERT [복구테이블] ON
INSERT INTO [복구테이블](컬럼1, 컬럼2, 컬럼3)
SELECT (컬럼1,컬럼2,컬럼3) FROM [백업테이블]
SET IDENTITY_INSERT [복구테이블] OFF
~~~
