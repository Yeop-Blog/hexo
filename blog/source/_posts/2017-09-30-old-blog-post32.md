---
title: 자주 쓰는 MySQL 명령어 정리
thumbnail: /images/mysql_thumbnail.jpg
date: 2017-09-30 19:04:00
categories:
- DB
- MySQL
tags:
---
**# root암호설정 - root로 로그인하여 해야함**  
% mysqladmin -u root password '변경암호'  
% mysqladmin -u root -p기존암호 password '변경암호'  

**root암호변경설정**  
PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !  
This is done with:  
/usr/bin/mysqladmin -u root -p password 'new-password'  
/usr/bin/mysqladmin -u root -h ns.moyiza.net -p password 'new-password'

**DB작업**  
DB생성: mysql> create database DB명 ( or % mysqladmin -u root -p create DB명 )  
DB삭제: mysql> drop database DB명  
DB사용: mysql> use DB명 (엄밀히 말하자면, 사용할 'default database'를 선택하는 것이다.)  
DB변경: mysql> alter database db명 DEFAULT CHARACTER SET charset (4.1이상에서만 available)

**MySQL 연결**  
mysql -u 사용자 -p DB명 ( or % mysqladmin -u root -p drop DB명 )

**데이터파일 실행(sql*loader기능)**  
mysql>load data infile "데이터파일" into table 테이블명 ;  
데이터파일에서 컬럼구분은 탭문자, Null값은 /n로 입력  
데이터파일의 위치는 /home/kang/load.txt 와 같이 절대경로로 지정할것.

**질의 파일 실행**  
쉘프롬프트상에서  
mysql -u 사용자 -p DB명 < 질의파일  
or  
mysql프롬프트상에서  
mysql> source 질의파일  

**쉘프롬프트상에서 질의 실행**  
``moyiza@nero board]$ mysql mysql -u root -pxxxx -e``  
~~~sql
INSERT INTO db VALUES(
'localhost', 'aaa', 'aaa',
'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y')
~~~

**사용자 생성 & 사용자에게 DB할당**  
~~~
shell> mysql --user=root -p mysql  

mysql> INSERT INTO user VALUES('localhost','사용자',PASSWORD('비밀번호'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y');
mysql> INSERT INTO user VALUES('%','사용자',PASSWORD('비밀번호'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y');

mysql> INSERT INTO db(Host,Db,User,Select_priv,Insert_priv,Update_priv,Delete_priv,Create_priv,Drop_priv) VALUES ('localhost','DB명','사용자','Y','Y','Y','Y','Y','Y');
mysql> INSERT INTO db(Host,Db,User,Select_priv,Insert_priv,Update_priv,Delete_priv,Create_priv,Drop_priv) VALUES('%','DB명','사용자','Y','Y','Y','Y','Y','Y');

mysql> FLUSH PRIVILEGES; (or shell prompt: mysqladmin -u root -pxxxx reload)
~~~

**CASE 2: GRANT명령을 이용한 사용자 생성(이 방법이 권장된다)**  
kang이라는 DB를 만들고, 이 DB를 아래에서 나열된 권한을 가진 kang이라는 사용자를 생성  
~~~
create database kang;
grant SELECT,INSERT,UPDATE,DELETE,CREATE,DROP on kang.* to kang@localhost identified by 'kang';
grant SELECT,INSERT,UPDATE,DELETE,CREATE,DROP on kang.* to kang@'%' identified by 'kang';

mysql> create database kang;
Query OK, 1 row affected (0.00 sec)

mysql> grant SELECT,INSERT,UPDATE,DELETE,CREATE,DROP on kang.* to kang@localhost identified by 'kang';
Query OK, 0 rows affected (0.00 sec)

mysql> grant SELECT,INSERT,UPDATE,DELETE,CREATE,DROP on kang.* to kang@'%' identified by 'kang';
Query OK, 0 rows affected (0.01 sec)
~~~

**여러가지 명령정리**  
``mysql> show variables;``  
: 서버의 variables(설정사항)출력  
``mysql> show variables like 'have_inno%';``  
: 조건에 맞는 variables만 출력  
``mysql> show databases;``  
: database목록  
``mysql> show tables;``  
: 현재DB의 테이블목록(temporary table은 출력하지 않음)  
``mysql> show tables from db명;``  
: 지정된 db명이 소유한 테이블목록  
``mysql> show tables like 'mem%';``  
: 조건에 맞는 테이블목록만 출력  
``mysql> show index from 테이블명;``  
: 인덱스 보기  
``mysql> show columns from 테이블명;``  
: 테이블구조(describe 테이블명, explain 테이블명)  
``mysql> show table status;``  
: 현재 DB의 테이블들의 상태(row수,table type,row길이,..)  
``mysql> show table status from db명;``  
: 지정된 DB의 테이블들의 상태(row수,table type,row길이,..)  
``mysql> show create table 테이블명;``  
: 해당 테이블 생성 SQL문 출력  
``mysql> rename table 테이블1 to 테이블2;``  
: 테이블명 변경(ALTER TABLE 테이블1 RENAME TO 테이블2)  
``mysql> rename table 테이블1 to 테이블2, 테이블3 to 테이블4;``  
: rename multiple tables  
``mysql> rename table db1명.테이블명 to db2명.테이블명;``  
: 테이블을 다른 DB로 이동  
``mysql> alter table 테이블명 add 컬럼명 데이터타입;``  
: 컬럼추가  
``mysql> alter table 테이블명 del 컬럼명;``  
: 컬럼제거  
``mysql> alter table 테이블명 modify 컬럼명 컬럼타입;``  
: 컬럼명에 지정된 컬럼타입의 변경  
``mysql> alter table 테이블명 change old컬럼명 new컬럼명 컬럼타입;``  
: 컬럼명 변경  
``mysql> alter table 테이블명 type=innodb;``  
: 테이블type변경  
``mysql> create table 테이블명(..) type=heap min_rows=10000;``  
: 10000row를 수용할 수 있을 만큼 메모리할당(heap type이므로)  
``mysql> select version();``  
: MySQL서버버전 출력  
``mysql> create table 테이블2 as select * from 테이블1;``  
: 테이블1과 동일한 테이블 생성(with 데이터, as는 생략가능)  
``mysql> create table 테이블2 as select * from 테이블1 where 1=2;``  
: 테이블1과 동일한 구조의 테이블 생성(without 데이터, 1=2는 0으로 할수도 있다.)  
``mysql> insert into 테이블2 select * from 테이블1;``  
: 테이블1의 데이터를 테이블2에 insert

**테이블이 존재여부 파악**  
~~~
DROP TABLE IF EXISTS 테이블명;
CREATE TABLE 테이블명 (...);
~~~
프로그래밍 언어에서 COUNT(\*)를 사용하여 질의가 성공하면 테이블이 존재함을 파악할 수 있다.  
ISAM, MyISAM의 경우 COUNT(\*)가 최적화되어 상관없으나, BDB, InnoDB의 경우 full scan이 발생하므로 사용하지 마라.  
대신 select * from 테이블명 where 0; 을 사용하라.  
질의가 성공하면 테이블이 존재하는 것이고, 아니면 존재하지 않는 것이다.

**접속**  
``mysql {-h 접속호스트} -u 사용자 -p 사용DB``  
-h로 다른 서버에 존재하는 MySQL접속시 다음과 같이 MySQL DB에 설정해줘야 한다.  
~~~
mysql> INSERT INTO user VALUES('접근을 허용할 호스트ip','사용자',PASSWORD('비밀번호'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y', 'Y','Y','Y','Y');
mysql> INSERT INTO db(Host,Db,User,Select_priv,Insert_priv,Update_priv,Delete_priv,Create_priv,Drop_priv) VALUES('접근을 허용할 호스트ip','사용DB','사용자','Y','Y','Y','Y','Y','Y');
mysql> FLUSH PRIVILEGES; or 쉴프롬프트상에서 % mysqladmin -u root -p flush-privileges
~~~

**검색조건(where)**  
regular expression을 지원하다니 신기하군..  
``mysql> select * from work where 열명 regexp "정규표현식";``

**백업 & 복구**  
~~~
mysqldump {-h 호스트} -u 사용자 -p DB명 > 백업파일
mysql {-h 호스트} -u 사용자 -p DB명 < 백업파일

mysqldump -u root -p --opt db_moyiza > moyiza.sql
mysqldump -u root -p --opt db_board | mysql ---host=remote-host -C database (상이한 머쉰)
mysql -u moyiza -p db_moyiza < moyiza.sql

mysqldump -u root -p --opt db_moyiza | mysql ---host=ns.moyiza.net -C db_moyiza
~~~

테이블 생성구문만을 화면에서 보려면 다음과 같이 --no-data를 사용한다. 테이블명을 생략하면 모든 테이블 출력  
``mysqldump -u 유저명 -p --no-data db명 테이블명``

**테이블 검사**  
``isamchk``

**오라클 sysdate와 동일**  
``insert into test values('12', now());``

**유닉스 time()함수 리턴값 사용**  
~~~
FROM_UNIXTIME(954788684)
UNIX_TIMESTAMP("2001-04-04 :04:04:04")
~~~

**MySQL 디폴트 DB&로그파일 위치**  
/var/lib/mysql  
/var/lib디렉토리는 여러 프로세스들이 사용하는 데이터를 저장하는 일종의 파일시스템상의 데이터베이스라고 볼 수 있다.

**replace**  
해당 레코드 존재하면 update하고, 존재하지 않는다면 insert한다.(insert문법과 동일)  
``replace into test values('maddog','kang myung gyu')'``

**explain**  
explain 질의문: 지정한 질의문이 어떻게 실행될 건지를 보여줌  
~~~
mysql> explain select u.uid, u.name, a.name from sm_user u, sm_addr a where u.uid=a.uid;
+-------+------+-----------------+-----------------+---------+-------+------+-------+
| table | type | possible_keys | key | key_len | ref | rows | Extra |
+-------+------+-----------------+-----------------+---------+-------+------+-------+
| u | ALL | PRIMARY | NULL | NULL | NULL | 370 | |
| a | ref | sm_addr_uid_idx | sm_addr_uid_idx | 11 | u.uid | 11 | |
+-------+------+-----------------+-----------------+---------+-------+------+-------+
2 rows in set (0.01 sec)
~~~

**temporary table**  
크기가 큰 테이블에 있는 subset에 대한 질의라면 subset을 temporary table에 저장한 후 질의하는 것이 더 빠를 경우가 있다.  
temporary table는 세션내에서만 유효하고(현재 사용자만이 볼수 있다는 뜻), 세션종료시 자동적으로 drop된다.
~~~
create temporary table (...);
create temporary table (...) type=heap; //디스크가 아닌 메모리에 테이블 생성
~~~

존재하는 permanent table의 테이블명과 동일하게 생성할 수 있으며,
temporary table은 permanent table보다 우선시되어 처리된다.  
4.0.7의 감마버전에서 테스트하면 결과는 약간 달라진다. 버그인건지..
~~~
mysql> create table test (id varchar(10));
Query OK, 0 rows affected (0.01 sec)

mysql> insert into test values('moyiza');
Query OK, 1 row affected (0.00 sec)

mysql> create temporary table test(id varchar(10));
Query OK, 0 rows affected (0.00 sec)

mysql> select * from test;
Empty set (0.00 sec)

mysql> drop table test;
Query OK, 0 rows affected (0.00 sec)

mysql> select * from test;
+----------+
| id |
+----------+
| moyiza |
+----------+
1 row in set (0.00 sec)
~~~

**Table Type에 다른 Files on Disk**  
ISAM .frm (definition) .ISD (data) .ISM (indexes)  
MyISAM .frm (definition) .MYD (data) .MYI (indexes)  
MERGE .frm (definition) .MRG (list of constituent MyISAM table names)  
HEAP .frm (definition)  
BDB .frm (definition) .db (data and indexes)  
InnoDB .frm (definition)

보통 mysqldump를 사용하여 백업을 수행하여 다른 DB서버에 데이터를 restore하면 된다.  
MySQL은 별다른 작업없이 데이터파일을 단순히 복사(copy)하는 것만으로도 다른 서버에 DB을 이동시킬 수 있다.  
하지만, 이런 방식이 지원되지 않는 table type도 있다.  

ISAM: machine-dependent format하기때문에..  
BDB : .db파일에 이미 테이블위치가 encode되어 있기때문에..  
MyISAM, InnoDB, MERGE :가능(machine-independent format)  

별다른 지정을 하지 않았다면 디폴트 TABLE type이 MyISAM이므로, 무난히 migration할 수 있다.  
floating-point컬럼(FLOAT,DOUBLE)이 있다면 이러한 방식이 실패할 수 도 있다.  

쉘에서는 mysql이 되는데 PHP에서 mysql.sock error를 내면서 MySQL이 안되는 경우 mysql.sock은 /tmp 아니면 /var/lib/mysql에 생기게 된다.  
나의 경우, /var/lib/mysql에 mysql.sock파일이 있는데 PHP에서는 /tmp에서 찾으려하면서 에러를 발생했다.  
/usr/bin/safe_mysqld파일에서 다음과 같이 수정한다.  
주석(#)이 달린 것이 원래것이고 그 밑에 있는것이 수정한 것이다.  

\# MYSQL_UNIX_PORT=${MYSQL_UNIX_PORT:-/var/lib/mysql/mysql.sock}  
MYSQL_UNIX_PORT=${MYSQL_UNIX_PORT:-/tmp/mysql.sock}

위와 같이 하니 /usr/bin/mysql이 /var/lib/mysql/mysql.sock에서 소켓파일을 찾으려 했다.  
socket file을 지정하는 --socket이라는 옵션으로 다음과 같이 지정하면 된다.  
``mysql --socket=/tmp/mysql.sock -u moyiza -p db_test``  

하지만 mysql실행시마다 이렇게 써줘야한다는 것이 상당히 귀찮다. 옵션이 바로 적용되게 설정하자.  
mysql은 설정사항을 다음 3가지 파일에서 검색한다.  

/etc/my.cnf global options(MySQL 전체적으로 사용되는 옵션 정의)
mysql-data-dir/my.cnf 특정 DB에 적용되는 option   (/var/lib/mysql/my.cnf)  
~/.my.cnf 사용자 각각의 설정('~'문자는 사용자의 홈디렉토리는 의미)

/usr/share/mysql디렉토리에 예제가 있으므로 참고한다.  
소켓파일의 지정은 다음줄을 넣어주면 된다.  
``socket = /tmp/mysql.sock``

== /etc/my.cnf예 ==  
~~~
# The following options will be passed to all MySQL clients
[client]
#password = your_password
port = 3306
socket = /tmp/mysql.sock

# Here follows entries for some specific programs

# The MySQL server
[mysqld]
port = 3306
socket = /tmp/mysql.sock
~~~


MySQL에서 통계처리시  
orderby, groupby 는 sort_buffer를 늘여준다.(show variables)  

live table(smslog)에서 모든 질의를 처리하지 말고 summary table에 질의결과를 저장해 재질의 처리한다.  
summary table이 heap-type table가 가능한지 확인할 것.
~~~
INSERT INTO tblTemp2 (fldID) SELECT tblTemp1.fldOrder_ID FROM tblTemp1 WHERE tblTemp1.fldOrder_ID > 100;
~~~

join이 subselect보다 빠르다.  
join시 사용되는 컬럼은 동일한 column type과 길이를 가져야만 최적의 속도를 보장한다.  
즉, 동일 column type이지만 길이가 다르다면(char(11), char(10)), 동일한 컬럼도메인으로 변경해주는 것이 좋다.  
where의 in은 optimize되어 있으므로 빠르다.  
insert,select는 동시에 수행가능하다.(어떻게?)  
explain으로 질의과정 점검  

varchar to/from char  
conversion varchar를 char로 변경할 경우 모든 컬럼타입을 동시에 변경해야 한다.  
반대의 경우, 하나만 char->charchar변경시 다른 모든 컬럼도 varchar로 변경됨  
참.. 특이하구만..
~~~
mysql> CREATE TABLE chartbl (name VARCHAR(40), address VARCHAR(80));
Query OK, 0 rows affected (0.05 sec)

mysql> desc chartbl;
+---------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name | varchar(40) | YES | | NULL | |
| address | varchar(80) | YES | | NULL | |
+---------+-------------+------+-----+---------+-------+
2 rows in set (0.03 sec)

mysql> alter table chartbl modify name char(40);
Query OK, 0 rows affected (0.02 sec)
Records: 0 Duplicates: 0 Warnings: 0

mysql> desc chartbl;
+---------+-------------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name | varchar(40) | YES | | NULL | |
| address | varchar(80) | YES | | NULL | |
+---------+-------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> alter table chartbl modify name char(40), modify address char(80);
Query OK, 0 rows affected (0.01 sec)
Records: 0 Duplicates: 0 Warnings: 0

mysql> desc chartbl;
+---------+----------+------+-----+---------+-------+
| Field | Type | Null | Key | Default | Extra |
+---------+----------+------+-----+---------+-------+
| name | char(40) | YES | | NULL | |
| address | char(80) | YES | | NULL | |
+---------+----------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql>
~~~

"For each article, find the dealer(s) with the most expensive price."

표준안
~~~sql
SELECT article, dealer, price
FROM shop s1
WHERE price=(SELECT MAX(s2.price)
FROM shop s2
WHERE s1.article = s2.article);
~~~

수정안(최적화)
~~~sql
CREATE TEMPORARY TABLE tmp (
article INT(4) UNSIGNED ZEROFILL DEFAULT '0000' NOT NULL,
price DOUBLE(16,2) DEFAULT '0.00' NOT NULL);

LOCK TABLES shop read;

INSERT INTO tmp SELECT article, MAX(price) FROM shop GROUP BY article;

SELECT shop.article, dealer, shop.price FROM shop, tmp
WHERE shop.article=tmp.article AND shop.price=tmp.price;

UNLOCK TABLES;

DROP TABLE tmp;
~~~

##### MySQL 특성정리
primary key, foreign key지원  
index 지원(15개컬럼, 256byte까지)  
MySQL에서의 Stored Script개념 => SQL server language  
commit-rollback개념 => lock tables(lock table test write -> 트랜잭션.. -> unlock tables)  
컬럼명길이: 64자까지, 컬럼 Alias: 256자까지  
not case-sensitive: keywords, functions, column, index명  
case-sensitive: database, table, alias명  
키워드,함수명은 대소문자구별이 없지만, db명과 table명은 Unix계열이라면 case-sensitive하다.  
(이는 오브젝트명이 OS의 fs에 따라 저장되기 때문이다. 서버의 lower_case_table_names 변수를 1로 설정하면 오브젝트명은 모두 소문자로 저장되므로 유닉스-윈도간 호환성을 높일 수 있다.)  

지원되지 않는 부분:  
Stored Procedure(5.0이상부터 지원된다고 함)  
View(5.0이상부터 지원된다고 함)  
Trigger(5.0이상부터 지원된다고 함)  
subquery(4.1이상부터 지원된다고 함)  
union, union all(4.0이상부터 지원됨)

[테이블 type에 따른 인덱스 특성]  
~~~
Index Characteristic ISAM MyISAM HEAP BDB InnoDB
NULL values allowed No Yes As of 4.0.2 Yes Yes
Columns per index 16 16 16 16 16
Indexes per table 16 32 32 31 32
Maximum index row size (bytes) 256 500 500 500/1024 500/1024
Index column prefixes allowed Yes Yes Yes Yes No
BLOB/TEXT indexes allowed No Yes(255 bytes max) No Yes (255 bytes max) No
~~~

인덱스 생성  
\- alter table을 이용한 인덱스 생성이 더 flexible함  
\- 인덱스명은 생략가능  

ALTER TABLE 테이블명 ADD INDEX 인덱스명 (인덱스컬럼);  
ALTER TABLE 테이블명 ADD UNIQUE 인덱스명 (인덱스컬럼);  
ALTER TABLE 테이블명 ADD PRIMARY KEY (인덱스컬럼);  
ALTER TABLE 테이블명 ADD FULLTEXT (인덱스컬럼);  

CREATE INDEX 인덱스명 ON 테이블명 (인덱스컬럼);  
CREATE UNIQUE INDEX 인덱스명 ON 테이블명 (인덱스컬럼);  
CREATE FULLTEXT INDEX 인덱스명 ON 테이블명 (인덱스컬럼);  

unique인덱스와 primary key인덱스와의 차이  
unique은 null허용하지만, primary key는 null허용 안함  
unique은 하나의 테이블에 여러개 올 수 있지만, primary key는 하나만 존재  

테이블생성시 지정  
~~~sql
CREATE TABLE 테이블명
(
... column declarations ...
INDEX 인덱스명 (인덱스컬럼),
UNIQUE 인덱스명 (인덱스컬럼),
PRIMARY KEY (인덱스컬럼),
FULLTEXT 인덱스명 (인덱스컬럼),
...
);
~~~

index prefix 생성  
\- 컬럼의 전체길이중 일부만 인덱스로 사용  
\- supported for ISAM, MyISAM, HEAP, and BDB tables, but not for InnoDB tables  
\- 지정되는 길이는 byte단위가 아닌 charater단위이므로, multi-byte character일 경우 주의  
\- blob, text 컬럼타입일 경우, index prefix 가 유용(255 길이까지 가능)  
~~~sql
CREATE TABLE 테이블명
(
name CHAR(30) NOT NULL,
address CHAR(60) NOT NULL,
INDEX (name(10),address(10))
);
~~~

인덱스 삭제  
~~~sql
DROP INDEX 인덱스명 ON 테이블명;
ALTER TABLE 테이블명 DROP INDEX 인덱스명;
ALTER TABLE 테이블명 DROP PRIMARY KEY;
~~~

OUTER JOIN  
[MySQL]
~~~sql
left outer joing : SELECT t1.*, t2.* FROM t1 LEFT OUTER JOIN t2 ON t1.i1 = t2.i2;
right outer joing: SELECT t1.*, t2.* FROM t1 RIGHT OUTER JOIN t2 ON t1.i1 = t2.i2;
~~~

[Oracle]
~~~sql
left outer joing : SELECT t1.*, t2.* FROM t1, t2 where t1.i1 = t2.i2(+);
right outer joing: SELECT t1.*, t2.* FROM t1, t2 where t1.i1(+) = t2.i2;
~~~

~~~sql
SELECT
student.name, student.student_id,
event.date, event.event_id, event.type
FROM
student, event
LEFT JOIN score ON student.student_id = score.student_id
AND event.event_id = score.event_id
WHERE
score.score IS NULL
ORDER BY
student.student_id, event.event_id;
~~~

**문장을 이용한 변수의 설정**  
현재 moyiza의 데이터베이스강좌게시판에 등록된 총 게시물은 43개이다. 43개의 강좌를 읽은 수(hit수)는 각각 다르다.  
평균 hit수를 구해 보자.  
~~~
mysql> select @total_hit := sum(hit), @total_record := count(*) from zetyx_board_database;
+------------------------+---------------------------+
| @total_hit := sum(hit) | @total_record := count(*) |
+------------------------+---------------------------+
| 3705 | 43 |
+------------------------+---------------------------+
1 row in set (0.00 sec)

mysql> select @total_hit/@total_record as 평균HIT;
+-----------------+
| 평균HIT |
+-----------------+
| 86.162790697674 |
+-----------------+
1 row in set (0.00 sec)
~~~
~~~sql
select substring(subject from 9) from zetyx_board_database where substring(subject, 1, 8) = '[ORACLE]';
~~~

보통 상용DBMS들이 row-level locking을 지원한다. 쉽게 말해 레코드단위로 락킹한다는 말이다.  
반면, MySQL의 MyISAM 테이블타입은 table-level locking을 사용한다.  
쉽게 말하면, insert, update, delete작업은 전체 테이블에 락을 걸고 처리된다는 것이다.  
row-level락보다 비효율적이지만,.. MySQL은 빠르기 때문에 이 단점이 상쇄된다.

Compressed MyISAM(packed MyISAM)  
정적인 테이블데이터는 압축하여 20-60%정도의 공간을 절약할 수 있다.  
Production데이터를 CD로 받아서 차후 디스크에 풀지 않고 CD자체로 바로 사용할 수도 있다.  
gzip등으로 백업받으면 이를 푸는 과정이 필요할 것이다.  
% myisampack moyiza.myi  

데이터베이스 게시판의 Merge Table에 좀 더 자세한 내용을 적어 두었다.

RAID Table  
1개의 테이블은 OS상에 3개의 파일로 구성된다.  
스키마파일(.frm), data파일(.myd), index파일(.myi)  
MySQL의 RAID테이블은 데이터파일(.myd)을 여러개의 파일들로 구성하는 것이다.

create table raid_test (...)  
type=myisam raid_type=striped raid_chunks=4 raid_chunsize=8

테이블을 4개의 데이터파일로 나누고, 8kb단위로(8kb stripe) 라운드로빈 방식으로 write가 이루어진다.
