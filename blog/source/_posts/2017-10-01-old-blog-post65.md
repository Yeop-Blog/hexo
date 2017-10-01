---
title: MSSQL PROCEDURE(프로시저)와 CURSOR(커서)의 활용
thumbnail: /images/mssql_thumbnail.jpg
date: 2017-10-01 22:22:00
categories:
- DB
- MSSQL
tags:
---
- 출처 : http://blog.naver.com/kbk9879/120126027566

set ANSI_NULLS ON  
set QUOTED_IDENTIFIER ON  
go  
<span style='color: red;'>--  실행문  
--  EXEC TEST_PROCEDURE '강길동', '05600000'  
--  현재의 DATABASE에 아래에서 선언한 내용이 없기 때문에 프로시저를 생성하면 오류 발생하므로  
--  아래의 구문에 맞게 DATABASE를 생성하거나 이미 만들어 놓은 DATABASE에 맞게 아래의 PROCEDURE내용을 바꿔야 함</span>  
CREATE PROCEDURE [dbo].[TEST_PROCEDURE] -- 프로시저를 생성할 때 사용(생성하고 또 실행하게 될 경우 이미 존재했다면서 오류 발생)  
ALTER PROCEDURE [dbo].[TEST_PROCEDURE]  -- 프로시저의 내용을 변경할 때 사용(CREATE를 한번 실행한 후 계속 ALTER로 사용하면 됨)  
<span style='color: red;'>--프로그램에서 넘겨 받을 변수선언</span>  
@strName    VARCHAR(10)   = '',   <span style='color: red;'>-- 1. 이름</span>  
@strNumber  VARCHAR(10)   = '',   <span style='color: red;'>-- 2. 번호</span>  
<span style='color: red;'>--프로그램으로 넘겨줄 변수선언</span>  
@Rtn INT = 0 OUTPUT, <span style='color: red;'>-- 3. 리턴 값(숫자)</span>  
@Msg VARCHAR(255) = '' OUTPUT <span style='color: red;'>-- 4. 리턴 값(문자)</span>  
AS  
BEGIN  
DECLARE @strTEL VARCHAR(11); <span style='color: red;'>-- 일반 변수</span>  

<span style='color: red;'>-- 변수 초기화(SET명령어는 해당 변수에 값을 넣어준다)</span>  
SET @Msg = '프로시저를 시작했습니다.'  
<span style='color: red;'>-- 이처럼 SELECT문의 결과를 SET명령어를 사용하여 변수에 저장할 수 있음</span>  
SET @strTEL = (SELECT HACKBUN  
FROM   STUDENT  
WHERE  STUDENT_NAME = @strName  
AND    STUDENT_NUMBER = @strNumber)  
<span style='color: red;'>-- CURSOR 생성</span>  
DECLARE CURSOR_NAME CURSOR FOR  
<span style='color: red;'>-- CURSOR안에서 사용할 값을 SETTING</span>  
SELECT STUDENT_TEL  
FROM   STUDENT  
WHERE  STUDENT_NAME = @strName  
AND    SEQ = @strNumber  
OPEN CURSOR_NAME <span style='color: red;'>--CURSOR_NAME은 임시로 만든 이름으로 사용자에 맞게 변경해주어도 된다  
--다만 FETCH문도 동일하게 바꿔주어야 하며, CLOSE, DEALLOCATE문에도 같은 이름을 사용해야 한다</span>  
FETCH NEXT FROM CURSOR_NAME INTO @strTEL <span style='color: green;'>----------------- 1</span>

<span style='color: red;'>-- FETCH_STATUS의 값이 성공(0)일때 WHILE문 실행</span>  
WHILE @@FETCH_STATUS = 0 BEGIN  
INSERT INTO ADDRESS (STUDENT_NAME, ADDRESS, TEL)  
VALUES (@strName, '대한민국', @strTEL);  
<span style='color: red;'>-- 이 부분에 새로운 CURSOR를 생성해서 사용해도 된다  
-- 즉, 다중 CURSOR문이 가능  
-- 이 안에 CURSOR를 생성하게 되면 결과는  
-- 첫번째 CURSOR에서 생성되는 값을 두번째 CURSOR에서 또 사용할 수 있어서 후처리를 할 때 편하다</span>  
FETCH NEXT FROM CURSOR_NAME INTO @strTEL <span style='color: green;'>------------------2</span>  
END;  
<span style='color: red;'>-- <span style='color: green;'>1, 2번</span>의 INTO뒤에 있는 변수는 CURSOR를 생성할 때 받는 값을 저장할 변수로써,  
-- 생성 부분의 SELECT문의 결과 개수와 1, 2의 FETCH문의 개수가 일치해야 됨  
-- <span style='color: green;'>1, 2번</span>은 똑같아야 한다.</span>  
CLOSE CURSOR_NAME <span style='color: red;'>-- CURSOR 닫기</span>  
DEALLOCATE CURSOR_NAME <span style='color: red;'>-- CURSOR 해체</span>  
SET @Msg = '정상적으로 처리가 되었을까요??'  
END
