---
title: MSSQL update-replace:기존의 데이터 변경하기
thumbnail: /images/mssql_thumbnail.jpg
date: 2017-10-02 14:29:47
categories:
- DB
- MSSQL
tags:
---
* 출처 : http://www.happyjung.com/bbs/board.php?bo_table=lecture&wr_id=1096

특정 컬럼의 문자들을 부분적으로 변경하고 싶을때 자바, 오라클, mssql 도 replace함수를 사용합니다.

##### 사용법  
replace( '대상문자열', '기존데이터', '바꿀데이터')  
select replace([칼럼명], '기존데이터', '바꿀데이터'), * from [테이블명]  
update [테이블명] set [컬럼명] = replace([컬럼명],'기존데이터','바꿀데이터')

예1) 일반컬럼  
subject 라는 칼럼에 '345' 를 'asas' 로 변경  
변경될 자료 미리 확인  
~~~sql
select replace(subject, '345', 'asas'), * from tblBoard where bdOptIdx = '68'
~~~

위에서 변경될 자료를 미리 본후 이상없으면 아래 쿼리 실행
~~~sql
update tblBoard set subject = replace(subject, '345', 'asas') where bdOptIdx = '68'
~~~

예2) 숫자컬럼  
regDate 라는 datetime 컬럼에 '2012-01-17 12:22:35:66' 의 자료에서
2012-01-17 만 2008-03-21 로 변경하고자 할때
~~~sql
select replace(regDate, '2012-01-17', '2008-03-21'), * from tblBoard where bdOptIdx = '68'

update tblBoard set regDate = replace(regDate, '2012-01-17', '2008-03-21') where bdOptIdx = '68'
~~~
요렇게 하면 변경이 안됩니다.  
날짜 형식은 저장되는 순서가 다르기 때문에 아래와 같이 convert 함수를 함께 사용해야 합니다.
~~~sql
update tblBoard set regDate = replace(convert(char(10), regDate, 112), '20120117', '20080321') where bdOptIdx = '68'

update tblBoard set regDate = replace(convert(char(10), regDate, 20), '2012-01-17 13:50:45', '2008-03-21 13:50:45') where bdOptIdx = '68'

update tblBoard set regDate = replace(convert(char(10), regDate, 20), '2012-11-05', '2012-07-09') where bdOptIdx ='4' and bdidx = '17'
~~~
결과값이 아래와 같이 보여도 정상변경된것입니다.  
(186 row(s) affected)

관련자료  
http://ellieya.tistory.com/66  
http://blog.naver.com/westlee25/150078828020
