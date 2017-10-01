---
title: Oracle ALTER 사용법 및 HINT 사용법
thumbnail: /images/oracle_thumbnail.jpg
date: 2017-10-01 21:31:00
categories:
- DB
- Oracle
tags:
---
1. **테이블 primary key drop**  
alter table 테이블명 drop primary key;  
ex) ``alter table bbs drop primary key;``

2. **해당 테이블 primary key 값 변경**  
alter table 테이블명 add constraint 인덱스명 primary key(인자1, 인자2, 인자3);  
ex) ``alter table bbs add constraint bbs_no_pk primary key(no);``

3. **오라클 SQL 힌트 사용법**  
~~~sql
SELECT /*+FIRST_ROWS(page_size)*/ BONE_TAB.ROW_NUM, FLESH_TAB.*
FROM ( SELECT /*+INDEX_DESC(table_name index_name)*/
ROWNUM AS ROW_NUM, ROWID AS ROW_ID
FROM table_name
WHERE ROWNUM < page_num * page_size + 1 ) BONE_TAB
INNER JOIN table_name FLESH_TAB
ON BONE_TAB.ROW_ID   = FLESH_TAB.ROWID
WHERE BONE_TAB.ROW_NUM > ( page_num - 1 ) * page_size

SELECT *
FROM ( SELECT /*+ INDEX_DESC(테이블명 인덱스명)  */
article_id,
title,
date
ceil( rownum / 한화면당 갯수 ) as page
FROM articles
WHERE 조건들....
) WHERE page = 출력하고 싶은 페이지번호
~~~
- 예제 쿼리  
~~~sql
select /*+ INDEX_ASC(bbs bbs_no_pk) */
rownum,
no,
title,
name
from bbs
~~~
