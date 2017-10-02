---
title: Oracle 트리거 작성시 Exception 에러 발생 확인 방법
thumbnail: /images/oracle_thumbnail.jpg
date: 2017-10-02 14:27:07
categories:
- DB
- Oracle
tags:
---
- 트리거에서 Exception 발생 에러 확인 하는 방법.
``dbms_output.put_line('Exception:'||SQLERRM);``
