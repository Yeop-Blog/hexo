---
title: 자바 성능을 결정짓는 코딩 습관 튜닝 이야기 요약
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 12:12:17
categories:
- Tip's
tags:
---
* 출처 : http://blog.naver.com/moonko1/90107818181

자바 성능을 결정짓는 코딩 습관 튜닝 이야기 요약

1. 너무나 많은 패턴을 사용하지 말라  
\- 꼭 필요한 패턴만 사용하라
<br>
2. 데이터 처리할때 TO(Transfer Object)패턴(vo패턴)을 사용하고, 아니면 Collection 관련 클래스 이용하라.
<br>
3. 서비스 로케이터(Service Locator)패턴은 적용하면 대기시간을 줄수 있다.
<br>
4. 명명 규칙을 잘 지켰는가?
<br>
5. 필요한 부분에 예외 처리는 되어 있는가?
<br>
6. 예외 화면은 지정되어 있는가?
<br>
7. 예외처리를 e.printStackTrace()해서 서버에 부하를 주지 말자
<br>
8. System.gc()메소드를 이용해서 가비지콜렉션을 지운다고 서버를 다운시키지말라
<br>
9. System.exit()메소드를 사용해서 프로세스를 죽이는 일이 없도록 하자
<br>
10. String클래스로 문자열을 코딩을 하지 말고 StringBuffer, StringBuilder로 클래스를 만들어서 사용하자
<br>
11. 무한 루프로 빠질수 있는 코드가 있는지 확인해보자(While)
<br>
12. Static 남발하지 말자(모르면 쓰지 말자)
<br>
13. 필요없는 Synchronized블록을 사용하지 말자(성능저하 원인)
<br>
14. IO가 계속발송하도록 개발되는지 확인해보자(NIO로 변경하자)
<br>
15. 필요없는 로그 파일은 제거하자(System.out, DEBUG, LOG)
<br>
16. jsp에 정적인 include를 사용하자(동적인 include는 사용하지 말자)
<br>
17. 자바 빈즈를 너무 많이 사용하지 말자(TO패턴으로 변경하자)
<br>
18. 태그 라이브러리는 너무 많이 사용하지 말자
<br>
19. EJB는 적정하게 사용하라
<br>
20. 이미지 서버를 사용할수 있는 환경인지 확인해보라
<br>
21. 사용중인 프레임웍은 검증되었는지 확인해보라
<br>
22. 적절한 JDBC 드라이버를 사용해라
<br>
23. DB Connection, Statement, ResultSet은 Close()되었는지 확인하라  
\- finally 구문에 반드시 close()해야 한다
<br>
24. DB Connection Pool을 잘 사용해야 한다.
<br>
25. ResultSet.last() 메소드를 사용하지 말라
<br>
26. statement보다는 PreparedStatements 사용하는 것이 더 좋다.
