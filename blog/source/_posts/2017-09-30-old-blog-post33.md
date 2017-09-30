---
title: DB LOCK 걸린것을 확인하는 쿼리문
thumbnail: /images/tip_thumbnail.jpg
date: 2017-09-30 20:23:00
categories:
- Programming
- Tip's
tags:
---
~~~sql
SELECT   
    username un, osuser ou, s.SID SID, s.serial# ser, l.TYPE ty,
         DECODE (lmode,
                 1, 'NONE',
                 2, 'RS',
                 3, 'RX',
                 4, 'S',
                 5, 'RSX',
                 6, 'X'
                ) mh,
         o.NAME ob, id1,
         DECODE (request,
                 1, 'NONE',
                 2, 'RS',
                 3, 'RX',
                 4, 'S',
                 5, 'RSX',
                 6, 'X'
                ) mr
    FROM v$lock l, v$session s, SYS.obj$ o
   WHERE l.SID = s.SID AND l.id1 = o.obj#(+) AND username IS NOT NULL
ORDER BY SID
~~~
