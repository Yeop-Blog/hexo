---
title: 이클립스(Eclipse)에서 SVN ID 변경하는 방법.
thumbnail: /images/ide_thumbnail.jpg
date: 2017-10-01 17:27:00
categories:
- Programming
- IDE's
tags:
---
- 출처 : http://blog.naver.com/ambion/50144389388

<첫번째 방법>  
C:\Users\<span style='color: #0075c8; font-weight: bold;'>본인컴퓨터이름</span>\AppData\Roaming\Subversion 에 가서 하위 파일들을 지우고 이클립스를 재시작.

<두번째 방법>  
통째로 받은 eclipse\configuration\org.eclipse.core.runtime 폴더를 보면 .keyring이라는 파일을 삭제후 이클립스 재시작.
