---
title: ORA-01861:literal does not match format string 에러 해결법
thumbnail: /images/oracle_thumbnail.jpg
date: 2017-09-30 21:16:00
categories:
- DB
- Oracle
tags:
---
- 출처 : http://blog.naver.com/kkh2004?Redirect=Log&logNo=120145122658

조건절 WHERE <span style="color: red">TO_CHAR</span>(START_DATE,"YYYY-MM-DD") = <span style="color: red">TO_DATE</span>("2007-08-31","YYYY-MM-DD")  
이부분에서 왼쪽은 char타입 오른쪽은 date타입..

일반적으로 토드에서는 실행되지만 자바 또는 다른 응용프로그램에서는 에러발생할 수 있음  
그래서 조건절에서는 둘다 같은 타입으로 변경해줘함.

---

JDBC를 통한 SQL Insert 를 할경우 다음과 같은 에러 메시지가 발생한다.  
java.sql.SQLDataException: ORA-01861: literal does not match format string(스트링이 형식에 맞지 않는다....)

TOAD나 Orange등 DB Tool을 사용하여 SQL Insert 할경우는 정상이다

이런 경우, 사용하는 WAS 계정의 .profile에 한글설정이 제대로 안된 경우가 대부분이다.  
.profile에 아래와 같이 한글 캐릭터셋 설정부분 추가후 WAS를 재기동 해주면 문제는 깨끗이 해결된다

**# TESTSvr#]  ./.profile (.profile 적용)**  
**# TESTSvr#] vi .profile**  
<span style="color: red; font-weight: bold;">export LANG=ko_KR.eucKR</span>

크론탭일 경우 굳이 was를 재기동 안해주고 실행되는 bat파일에 <span style="color: red">export LANG=ko_KR.eucKR</span> 만 추가 시켜도 됨
