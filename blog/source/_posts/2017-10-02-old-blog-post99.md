---
title: ssh서버가 비밀번호를 거부했습니다. 다시 시도하십시오.
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 15:22:18
categories:
- Tip's
tags:
---
- 출처 : http://dolbak.egloos.com/v/1874068

##### 증상
root계정으로 ssh로그인 실패.  

##### 원인
ssh설정에서 root로그인이 허용되지 않음.

##### 해결법
1. vi /etc/ssh/sshd_config
2. PermitRootLogin no 설정부분의 no를 yes로 변경.
3. kill -HUP sshd_pid   (ssh프로세스 재시작)
