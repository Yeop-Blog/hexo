---
title: Cookie값을 이용해 게시물 조회수 중복처리가 안되게끔 하는 방법
thumbnail: /images/lang_thumbnail.jpg
date: 2017-10-02 11:49:05
categories:
- Language
- JSP
tags:
---
- 아래 부분을 컨트롤단에 넣어서 활용하면 된다.  
다만, 현재 방법으로써는 계속 bbsSeq값 관련된 쿠키값이 늘어난다는 단점이 있다. 이 부분에 대한 개선이 필요하다.
~~~
int countCheck = 0;

Cookie[] cookies = req.getCookies();
  if (cookies != null) {
   for (int i = 0; i < cookies.length; i++) {
    if(cookies[i].getName().equals("bbsSeq"+bbs.getBbsSeq())){
     countCheck = 0;
     break;
    }else{
     Cookie cookie = new Cookie("bbsSeq"+bbs.getBbsSeq(), String.valueOf(bbs.getBbsSeq()));
     cookie.setMaxAge(60*60*24);
     cookie.setPath("/");
     res.addCookie(cookie);

     countCheck += 1;
    }
   }
  }

  //상세정보 조회시 카운트 증가
  if(countCheck > 0){
   bbsService.updateBbsViewCount(bbs);
  }
~~~
