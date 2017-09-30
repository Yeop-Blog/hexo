---
title: 프로토콜(Protocol)의 종류
thumbnail: /images/lang_thumbnail.jpg
date: 2017-09-30 20:44:00
categories:
- Language
tags:
---
##### 프로토콜
- 통신규약이라는 뜻.. 이런이런방식으로 대화하자는 약속..대화방법..

- **DHCP**(Dynamic Host Configuration Protocol)  
다이나믹 호스트 컨피규어 프로토콜  
사용자가 많은 환경에서 자동으로 ip를 할당해주어 관리를 편하게 해주며
ip한계를 도와주는 프로토콜  
영구적인 IP 주소를 필요로 하는 웹서버에 대해서는 정적인 주소를 제공한다.

- **SSL**(Secure Socket Layer)  
시큐어 소켓 레이어  
네트워크 내에서 메시지 전송의 안전을 관리하기 위해 만들어진 프로그램 계층.  
전자상거래 등의 보안을 위해 개발되었다.

- **TLS**(Transport Layer Security)  
트랜스포트 레이어 시큐어리티  
**SSL**의 뒤를 잇는 표준.

---

- **HTTP**(**H**yper**T**ext **Transfer Protocol**) : 사용포트 **80**  
하이퍼텍스트 트랜스퍼 프로토콜....  
**웹(인터넷)**상에서 정보를 주고받기 위한 프로토콜(대화방법).

- **HTTPS**(**S**ecure **H**yper**T**ext **Transfer Protocol**): 사용포트 **443**  
시큐어 하이퍼텍스트 트랜스퍼 프로토콜  
소켓 통신에서 일반 텍스트를 이용하는 대신에, **SSL**이나 **TLS** 프로토콜을 통해 세션 데이터를 암호화한다.  
따라서 데이터의 적절한 보호를 보장한다.  
전자상거래에 널리 쓰인다.

- **FTP**(<span style="color: #009e25; font-weight: bold;">File Transfer Protocol</span>) : 사용포트 **21**  
파일 트랜스퍼 프로토콜.....  
파일 업로드 다운로드를 목적으로 하는 프로토콜(대화방법).

- <span style="color: #ef007c; font-weight: bold;">S</span>**FTP**(**S**ecure <span style="color: #009e25; font-weight: bold;">File Transfer Protocol</span>): 사용포트 **22**  
시큐어 파일 트랜스퍼 프로토콜.....  
보안FTP.....일반적인 FTP와 달리 데이터 전송시 암호화 하는 프로토콜(대화방법).

- <span style="color: #ef007c; font-weight: bold;">T</span>**FTP**(**T**rivial <span style="color: #009e25; font-weight: bold;">File Transfer Protocol</span>): 연결포트는 **UDP 69**, 데이터 전송은 **UDP 1390**  
트리비얼 파일 트랜스퍼 프로토콜.....  
하찮은FTP.....-\_-;;;; 왜냐.... FTP보다 기능이 조금 덜해서.....  
디렉토리를 보여주지 않아도 되는곳에 사용..... ㅋㅋㅋ 하찮은 녀석.....
