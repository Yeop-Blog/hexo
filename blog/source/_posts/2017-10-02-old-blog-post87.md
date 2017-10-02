---
title: 윈도우 소켓이 80포트를 물고 있어서 Windows socket error가 발생시
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-02 14:28:02
categories:
- Tip's
tags:
---
- 출처 : http://allreview.co.kr/130175671911

TCP/IP, 소켓(winsock), DNS 초기화 명령어

IP주소는 정상으로 할당 받았으나, 인터넷 페이지가 열리지 않거나 특정 프로그램이 인터넷 접근이 안되는 경우.  
CMD를 관리자 권한으로 실행 후, 아래 명령어를 입력합니다.

**TCP/IP 재 설정** - http://support.microsoft.com/kb/299357  
``netsh int ip reset log.txt``

**winsock 연결 재 설정** - http://support.microsoft.com/kb/811259  
``netsh winsock reset``

**DNS 재 설정**  
``ipconfig /flushdns``

일반적으로 TCP/IP 를 재 설정하면 복구됩니다.  
작업 진행 전 반드시 시스템 복원 지점을 생성하십시오.
