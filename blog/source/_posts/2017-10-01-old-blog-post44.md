---
title: 백업 임시 테이블 생성시 쿼리문
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-01 16:41:00
categories:
- Tip's
tags:
---
\* Create Table **AS** ...    
ex) Create ExamTable AS Select(~~~~~);  
: 실제 운영서버에서 테스트를 해볼시 본 DB를 갖고 update, delete 등을 했다간 큰일나므로.. 같은 열의 이름과 내용을 가진 테이블을 하나 더 만들어 처리를 한다.  
\- 뒤에 Where 1 = 0; 을 추가하면 열만 복사되고 내용은 빈 값으로 만들어진다.
