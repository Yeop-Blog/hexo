---
title: MSSQL IDENTITY값(시퀀스) 초기화
thumbnail: /images/mssql_thumbnail.jpg
date: 2017-10-02 15:16:09
categories:
- DB
- MSSQL
tags:
---
- 출처 : http://jin5.blogspot.kr/2009/01/mssql-identity.html

보통 PK 값으로 사용하는 항목은 자동증가(auto_increment ; identity) 로 지정하는 경우가 많습니다. 테스트용으로 데이타를 넣고 삭제하다 보면 지정된 시작번호(예를 들면, 1) 부터 나오지 않게 됩니다. 이것을 서버에서 그 번호를 관리하고 있기 때문입니다.  
사실 반드시 1번부터 시작하지 않아도 상관은 없는데 궂이 1부터 나오도록 하고자 하는 욕심이 있습니다. 그럴 경우 다음처럼 하시면 됩니다.  
1. 일단 모든 데이타를 삭제할 것이고요
2. 쿼리창에서 다음의 쿼리문을 작성하고 실행시킵니다.
``DBCC CHECKIDENT( [table_name] , RESEED, 0 )``
예를 들어 테이블명이 member 라면  
``DBCC CHECKIDENT( member , RESEED, 0 )``
다음부터는 insert 로 들어가는 데이타의 자동증가 항목은 1부터 들어갑니다.  
'0' 을 '100' 으로 주면 다음부터는 101번부터 들어가게 됩니다.
3. 자동 증가 되는 수치는 다음과 같이 쿼리문 작성 후 실행
``alter table 테이블명 auto_increment=1``  
숫자는 시작하고 싶은걸로 하세요.
