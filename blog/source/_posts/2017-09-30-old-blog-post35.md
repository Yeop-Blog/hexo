---
title: 윈도우 탐색기에서 우측 클릭으로 바로 cmd창 실행하기
thumbnail: /images/tip_thumbnail.jpg
date: 2017-09-30 20:34:00
categories:
- Tip's
tags:
---
* 출처 : http://sojiyoung.tistory.com/28

개발하다 보면 Windows에서 콘솔창을 자주 사용하게 된다.  
콘솔창을 '시작'->'실행'->'cmd'로 호출하게 되면 처음 실행되는 디렉토리가 고정되어 있어서 매번 'cd'명령어로 디렉토리 이동을 해줘야 하는 불편함이 있다.

아래 레지스트리는 탐색기에서 폴더에서 우측 버튼을 눌러 'cmd'를 호출하는 레지스트리다.  
이렇게 실행된 콘솔창은 경로가 폴더의 경로로 되어 있어서 매번 'cd'명령어로 디렉토리 이동을 하지 않아도 되어 편리하다.

이런 방법은 google에서 'Command Prompt Here'로 검색해도 무수히 많이 나오는데, 레지스트리 이용 방법은 다 비슷하다.  
오래전에 어디선가 다운받아 사용 하던것인데 가독성을 높이려고 메뉴 내용을 한글로 바꾸었다.

[CmdContextInstall.reg 다운로드](https://yeop-blog.github.io/downloads/CmdContextInstall.zip)

~~~
REGEDIT4
; 탐색기에서 폴더 선택하고 이 경로에 도스창을 연다.-설치버전
; 윈도2000, NT: "%SystemRoot%\system32\cmd.exe" /k cd /d "%1"의 경로에서 CMD.EXE를 찾는다.
; 윈도 2000에서 테스트 되었고 다른 OS에서는 적절히 고쳐서 쓰면 될것.[HKEY_CLASSES_ROOT\Folder\shell\Command Prompt Here]
@="CMD(도스창) 열기"[HKEY_CLASSES_ROOT\Folder\shell\Command Prompt Here\command]
@=hex(2):22,25,53,79,73,74,65,6d,52,6f,6f,74,25,5c,73,79,73,74,65,6d,33,32,5c,\
63,6d,64,2e,65,78,65,22,20,2f,6b,20,63,64,20,2f,64,20,22,25,31,22,00
~~~

[CmdContextUnInstall.reg 다운로드](https://yeop-blog.github.io/downloads/CmdContextUnInstall.zip)

~~~
REGEDIT4
; 탐색기에서 폴더 선택하고 이 경로에 도스창을 연다. - 삭제버전
; 윈도2000, NT: "%SystemRoot%\system32\cmd.exe" /k cd /d "%1"의 경로에서 CMD.EXE를 찾는다.
; 윈도 2000에서 테스트 되엇고 다른 OS에서는 적절히 고쳐서 쓰면 될것.

[-HKEY_CLASSES_ROOT\Folder\shell\Command Prompt Here]
~~~
