---
title: 코딩 표준(변수 명명법)
thumbnail: /images/lang_thumbnail.jpg
date: 2017-09-29 22:57:00
categories:
- Language
tags:
---
개발자마다 전부 다른 스타일인 부분인데 정리가 되어 있는게 있어서 퍼옵니다.  
뭐 소프트웨어공학 같은곳에서 나오는 이야기지만 참고하시면 도움이 될것 같습니다.

---
##### Naming Rule

1. PascalCasing (파스칼 케이싱)  
￭ 클래스, 열거형, 이벤트, 메서드 등의 이름을 만들 때에는 대문자로 시작하는 변수명을 사용한다.  
￭ 복합어일 경우 중간에 시작하는 새로운 단어는 대문자로 적는다.  
&nbsp;&nbsp;&nbsp;예) UtilityBox, MainFrame

2. CamelCasing (카멜 케이싱)  
￭ 메서드의 매개변수의 이름에 적용되는데 첫번째 문자는 소문자로 시작하고 복합어 일 경우 파스칼 케이싱과 동일하게 적용한다.  
￭ 동일한 이름을 가지는 두 항목을 구분하는 용도로도 사용한다.  
&nbsp;&nbsp;&nbsp;예) utilityBox, mainFrame

3. GNU Naming Convention  
￭ Linux의 프로젝트들은 GNU Naming Convention이라는 형태의 명명법을 주로 사용한다.  
￭ 모두 소문자를 사용하고 복합어 사이를 '\_'를 사용하여 연결한다.  
&nbsp;&nbsp;&nbsp;예) gtk_widget_activate

4. Hungarian notation (헝가리안 표기법)  
￭ Microsoft 의 개발자중 헝가리 사람의 프로그래머가 쓰던 변수 명명법으로 MS내부에서 따라쓰기 시작하던 것이 점차 전세계의 프로그래머들에게 널리 퍼져 이젠 프로그램 코딩시 변수 명명의 표준적인 관례가 되었다.  
￭ C#에서는 이러한 명명법을 사용하지 않고 있으며 주로 윈도우즈 프로그래밍에 사용된다.  
&nbsp;&nbsp;&nbsp;예) g\_bTrue  
￭ 첫글자 g는 전역변수, m은 멤버변수를 의미한다. 전역이나 멤버변수의 경우에는 그 다음에 \_ 를 적는다.  
￭ b는 Boolean타입을 의미하고 True가 의미있는 이름이다.  
&nbsp;&nbsp;&nbsp;예) nCnt  
￭ 전역이나 멤버변수가 아니므로 g_ 나 m_ 가 없다.  
￭ n과 i는 자연수를 뜻하며 i는 주로 인덱스에 사용하고, n은 카운트의 목적에 주로 사용한다.  
￭ 의미있는 이름이 길 경우에는 자음만을 사용한다.

5. BREW Naming Convention  
￭ BREW 는 Qualcomm에서 만든 플랫폼으로 국내의 휴대폰 제조사들은 초기부터 현재까지 이 코드들을 많이 사용하고 있다.  
￭ 기존 명명법을 조합한 형태로 변종 명명법이지만, 익숙함을 벗어나지 못하는 국내 제조사의 개발자들이 선호하는 형태이다.  
￭ 클래스나 인터페이스를 대문자나 파스칼 케이싱으로 앞에 두고, '\_' 이후에 다시 파스칼 케이싱 형태의 메서드 명을 적는다.  
&nbsp;&nbsp;&nbsp;예) IDISPLAY_ClearScreen

6. Constant (상수)  
￭ 거의 모든 명명법에서 상수를 표기하는 방법은 거의 동일하다.  
￭ 모든 문자를 대문자로 사용하는 GNU Naming Convention의 형태를 사용한다.  
&nbsp;&nbsp;&nbsp;예) DEFAULT_COUNTRY_CODE  
다양한 명명법들이 존재한다. 어떤 방법이 가장 좋다라는 것은 없다. 프로젝트의 상황에 가장 적합한 명명법을 팀에서 결정하는 것이다. 프로젝트의 초기에 명명법을 결정하고 모든 개발자들이 규칙을 따라 코드를 작성하는 것이다.

##### C Naming Rule

\- 코딩 이름 규칙  
￭ 전체적으로 자바 코딩 스타일을 따른다  
￭ 우선순위가 높다는 것은 먼저 시작한다는 뜻  

1. 변수  
￭ 일반적인 변수(i, j, tmp)는 그때 상황에 맞게 사용 (남발하지 말기)  
￭ 첫단어는 소문자로 시작하되 새로운 단어의 시작은 대문자 ( priceSum )  
￭ 정수(int, long)는 prefix가 없다 (int 와 long 구분에 신경쓰기)  
￭ 실수(float, double)는 각각 f, d 로 시작한다  
&nbsp;&nbsp;&nbsp;예) float fPriceSum, double dPriceSum  
￭ unsigned 형이면 정수, 실수 상관없이 u 가 붙는다  
&nbsp;&nbsp;&nbsp;예) int uPriceSum, long uPriceSum, float fUPriceSum, double dUPrice  
￭ 우선순위는 f = d > u  
￭ 문자형 변수는 ch 로 시작한다  
&nbsp;&nbsp;&nbsp;예) char ch, char chInput, char chOutput  
￭ 배열은 arr 로 시작한다  
&nbsp;&nbsp;&nbsp;예) int arrPriceSum[10], char arrAuthorName[10]  
￭ 포인터는 ptr 로 시작한다  
&nbsp;&nbsp;&nbsp;예) int \*ptrPriceNum, char, char \*ptrAuthorName  
￭ 외부변수는 g 로 시작한다  
&nbsp;&nbsp;&nbsp;예) unsigned int gUPriceNum, char \*gPtrAuthorName, char gArrAuthorName[10]  
￭ 정적변수는 st 로 시작한다  
&nbsp;&nbsp;&nbsp;예) float stFPriceNum, char \*stPtrAuthorName, char stArrAuthorName[10]  
￭ 정적외부변수는 gst 로 시작한다  
&nbsp;&nbsp;&nbsp;예) unsigned double gstDUPriceNum, char \*gstPtrAuthorName,  char gstArrAuthorName[10]  
￭ 구조체 멤버변수는 m 으로 시작한다  
&nbsp;&nbsp;&nbsp;예) int mPriceSum, char \*mPtrAuthorName, char mArrAuthorName[10]  
￭ 구조체 인스턴스변수는 stru 로 시작한다  
&nbsp;&nbsp;&nbsp;예) SPerson struPerson, SPerson \*ptrStruPerson  
￭ 파라미터는 x 로 시작한다  
&nbsp;&nbsp;&nbsp;예) int xPriceNum, char \*xPtrAuthorName  
￭ 우선순위는 g = st = gst = m = x > ptr = arr > stru > f = d > u

2. 상수, 매크로  
￭ 대문자  
￭ 단어와 단어 사이는 \_ 로 연결한다  
&nbsp;&nbsp;&nbsp;예) const double PI = 3.14; , #define MAX_SIZE 1024

3. 함수  
￭ 동사 + 목적어 이고 완전한 단어를 사용한다  
￭ 동사는 소문자이고 목적어의 시작은 대문자, 목적어 새로운 단어의 시작도 대문자  
&nbsp;&nbsp;&nbsp;예) char \*makeLinkedList(...) {...}

4. 구조체  
￭ 구조체명은 \_S 로 시작하고 단어의 시작은 대문자, 새로운 단어의 시작도 대문자  
￭ typedef 로 재정의 할때는 _ 만 없앤다.  
~~~
struct _SPerson {
...
};
typedef struct _SPerson SPerson;
~~~
5. 주석
~~~
 /*************************************************************  
 * NOTE ￭ programid.c
 *      blah blah blah ~
 * Author ￭ programer name
 * Since ￭ 작성일자
**************************************************************/
~~~

##### 코딩 표준 (HTML/ASP/JavaScript)  
일반적으로 웹서비스에서는 파일, 테이블, 필드, 변수 네이밍에 첫글자를 소문자로 쓰고  
복합단어를 대문자로 구분 (“itemAdd.asp”, “rsStudentList”, “mlHours” 등)하는 헝가리안 표기법을 사용한다.

1. 파일과 폴더 이름  
￭ 모든 폴더는 index.html(혹은 .shtml, .asp)파일을 포함하도록 한다.  
￭ 사이트는 논리적, 상속적인 방법으로 조직되어야 한다.  
￭ 한 디렉토리에 모든 파일을 집어넣지마라  
￭ 모든 파일이름은 소문자라 숫자로 시작한다.  
￭ 파일이름에서 숫자가 먼저 나오면 뒤에는 소문자를 쓴다  
&nbsp;&nbsp;&nbsp;예)  “2editImage.asp”  
￭ 복합 단어는 대문자로 구분한다 예)  “itemEdit.asp”).  
￭ 밑줄(”\_”)이나 대시(”-”)는 파일이름에 사용하지 마세요.  
￭ 파일이름에 공백을 사용하지 마세요.  
￭ 같은 그룹의 페이지들은 같은 단어나 문자열로 파일이름을 시작한다  
&nbsp;&nbsp;&nbsp;예)“itemAdd”, “itemAdded”, “itemEdit”, “itemEdited”  
 이렇게하면 서로 연관있는 페이지들을 찾기 편하다.  
￭ 서버측에서 포함되는 파일(모든 템플릿 기반 파일)에는 .shtml 을 확장자로 사용하고 .htm 이나 .html 을 사용하지 마라.  
￭ 파일이나 폴더이름 시작부분에 사용되는 축약어는 소문자로 표기한다  
&nbsp;&nbsp;&nbsp;예)“atecStaffList.asp”, “imcResources.shtml”

2. 폴더이름 표준  
￭ 이미지 파일은 “/images/.” 폴더에 저장한다.  
￭ 이미지가 적은 사이트라면, 이미지 폴더를 루트 폴더 바로 아래에 두고 사이트의 모든 이미지를 그 폴더에 저장한다.  
￭ 이미지가 많고 다단계의 페이지들이 있다면, 사이트의 각 하위 폴더마다 “images” 폴더를 만들어서 각 하위 페이지에서 사용하는 모든 이미지는 각 “images” 폴더에 저장하는게 좋다.  
￭ 큰 이미지 대신 작은 썸네일을 보여주는 사이트라면 모든 썸네일 이미지를 “images” 폴더 아래의 “thumbnails” 폴더에 저장한다. 썸네일 이미지의 파일명은 원래 크기의 이미지와 똑같게 한다.  
￭ 포함하는 파일은 루트 디렉토리 아래의 “/\_include/” 에 저장한다.  
￭ 자바스크립트 파일은 루트 디렉토리 아래의 “/\_scripts/” 에 저장한다.  
￭ CGI 스크립트는 루트 디렉토리 아래의 “/cgi-bin/” 에 저장하거나 스크립트가 사용되는 디렉토리에 저장한다.  
￭ 스타일시트 파일은 루트 디렉토리 아래의 “/\_styles/”에 저장한다.  
￭ 새 사이트를 개발하는데 사용되는 파일은 루트 디렉토리 아래의 “/\_dev/” 에 저장한다.

3. 변수명 (JavaScript, ASP)  
￭ 변수명은 헝가리안 표기법을 따릅니다.  
￭ 모든 이름은 소문자로 시작하도록 한다(숫자는 안됩니다).  
￭ 복합 단어 이름은 대문자로 구분하도록 한다예)  “firstName”).  
￭ 변수명에 밑줄(”\_”)이나 대시(”-”) 를 사용하지 마세요.  
￭ 설명이 없거나 심하게 축약된 이름은 피하도록 한다.  
￭ 변수가 정확히 무엇을 의미하는지 알 수 있도록 명명하는게 중요한다  
&nbsp;&nbsp;&nbsp;예)“firstName”을 “fn”으로 쓰지 마세요  
￭ “i”나 “x” 같은 이름은 “for” 반복문에만 쓰는게 좋다.

4. HTML/ASP 형식  
￭ 실제로 사용되는 페이지는 XHTML Transitional 규격을 만족하도록 해야한다.  
￭ 모든 ASP 코드는 (Response.Write 문 포함) 올바른 XHTML 코드를 만들어내야 한다.  
￭ 모든 ASP 명령과 문장은 첫글자를 대문자로 표기한다  
￭ 모든 접속은 포함되는 파일(inculde file)을 이용한다.  
￭ 대부분의 경우, 레코드 선언은 문서의 제일 위쪽 태그 이전에 위치시키세요.  
￭ 모든 레코드셋 이름은 “rs”로 시작한다 예)“rsItemInfo”  
￭ 접속을 사용하는 모든 페이지는 페이지의 마지막에서 접속을 종료해주세요 (태그 아래).  
￭ 모든 질의문은 구분자가 있어야 한다  
&nbsp;&nbsp;&nbsp;예)“itemEdit.asp?itemID=33″, 이건 안됨 “itemEdit.asp?33″  
￭ 변수, 레코드셋, 질의 구분자 이름은..  
￭ 소문자로 시작한다  
￭ 변수 내에서의 단어 구분은 대문자를 이용한다  
&nbsp;&nbsp;&nbsp;예)  “userFirstName”  
￭ 밑줄은 사용하지 않는다  
￭ 축약어가 첫글자부터 쓰이면 축약어 전체를 소문자로 표기한다  
&nbsp;&nbsp;&nbsp;예)  “sqlString,” 이건 안됨 “sQLString”  
￭ 매우 짧은 구문을 제외한 모든 구문은 어떤 목적으로 작성되었는지 설명하는 주석을 달아두어야 한다.  
￭ 여러줄에 걸친 구문은 코드와 분리하는 묶음기호를 이용해서 명확히 작성하도록 한다.  
~~~
< %
If aspStatement Then
?
?
End If
%>
~~~

5. Cascading Style Sheets  
￭ 스타일 이름은 모두 소문자로 한다 (XHTML에선 대문자가 허용되지 않는다), 밑줄(”\_”)도 안됩니다.  
￭ 포맷팅을 위한 스타일은 배타적으로 사용한다 (모든 <font>태그는 제거되어야 한다).  
￭ 기존의 HTML 요소를 적극 활용한다. h1 태그로 필요한 스타일을 만들 수 있는데도 .head1 클래스를 추가하지 마세요.  
￭ 이미 있는 스타일시트를 활용한다. 정말로 필요할 경우가 아니라면 새 스타일을 만들지 마세요. 링크의 스타일은 전체에 적용한다.  
￭ 스타일 시트의 스타일을 알파벳순으로 정렬해놓으면 유지보수 측면에서 좋다.  
￭ 특정 페이지에만 사용하는 스타일은 페이지 헤더에서 정의한다.

6. 자바스크립트  
￭ 정확한 동작을 위해서 모든 script태그는 type 과 language 를 포함해야 한다.  
￭ language=”JavaScript” type=”text/JavaScript”. 를 사용한다.  
￭ JavaScript 변수는 ASP 변수 네이밍 규약을 따릅니다.  
￭ 작성된 자바스크립트 (한페이지에서만 사용되는)는 사용될 페이지의 헤더에 위치시킨다.  
￭ 여러 페이지에서 사용될 함수는 .js 파일로 만드세요. 우리의 표준에서는 .js 파일을 root/\_scripts/ 폴더에 저장한다.  
￭ 자주 사용하는 함수도 자바스크립트 파일에 모아놓을 수 있다. 이 파일들은 절대경로로 참조한다.

7. SQL 형식  
￭ 모든 SQL 예약어는 대문자로 입력한다  
  예) SELECT * FROM tableName WHERE dtStartDate > ‘3/3/03’.  
￭ 여러 테이블을 쿼리할때는 JOIN 문을 이용한다. 비표준 다중 테이블 쿼리는 자제해주세요.

8. SQL 테이블과 필드  
￭ 테이블과 필드 이름은… 소문자로 시작한다.  
￭ 변수명 내에서의 구분은 대문자를 이용하도록 한다  
&nbsp;&nbsp;&nbsp;예)  “userFirstName”  
￭ 밑줄(”\_”)은 사용하지 않는다.  
￭ 축약어가 처음에 사용되면 소문자로 표기한다  
&nbsp;&nbsp;&nbsp;예)  “sqlString”, 이건 안됨 “sQLString”  
￭ 같은 그룹의 테이블들은 같은 문자열로 시작하도록 한다  
&nbsp;&nbsp;&nbsp;예)  “mlHours”, “mlPlatform”, “mlService”  
￭ 테이블 이름에 복수형은 사용하지 않는다.  
￭ 테이블 이름과 필드 이름에 숫자는 사용하지 않는다.  
￭ 필드 이름의 첫문자를 자료형으로 표기한다.  
￭ 문자열 자료형은 (char, varChar, etc.) “s” 로 시작한다  
&nbsp;&nbsp;&nbsp;예)“sFirstName”  
￭ 정수 자료형은 “i”로 시작하되 (“iFacilityID”), 주키(primary key)로 사용되는 필드라면 “ID”로 명명한다.  
￭ 실수형은 “n” (for “numeric”) 으로 시작한다.  
￭ 날짜형은 “dt” 로 시작한다.  
￭ 비트형은 “b” 로 시작한다.  
￭ 모든 테이블은 “ID”라는 이름의 주키(primary key) 필드를 가지고 있어야 한다. 다중 테이블 쿼리에서 필드가 테이블 이름과 함께 구분(“userList.ID”)되므로 테이블 이름과 같이 명명하지 마세요  
&nbsp;&nbsp;&nbsp;예)  “ID,” 이건 안됨 “userListID”  
￭ 뷰와 스토어드 프로시저는 “view”와 “proc” 로 시작해서 테이블과 구분짓는다  
&nbsp;&nbsp;&nbsp;예)  “viewCurrentStaff,” “procCalcDaysLeft”
