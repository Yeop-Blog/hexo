---
title: XML, JSON, BSON, MSGPACK 장,단점 비교
thumbnail: /images/lang_thumbnail.jpg
date: 2017-09-29 22:48:00
categories:
- Language
tags:
---
##### XML
- 장점  
\- 나온지 10년이 넘어 엄청나게 널리 쓰이고 있음

- 단점  
\- 의미를 확인하기 위한 불필요한 TEXT(시작태그 및 닫는태그 등)가 포함 됨  
\- DTO를 사용하기 위해선 반드시 파싱과정을 거쳐야 함

##### JSON
- 장점  
\- 대부분의 언어별 lib지원  
\- 불필요한 XML대비 TEXT가 없어 패킷용량 감소  
\- 대부분의 언어의 기본 Collection type으로 바로 사용 가능

##### BSON
- 장점  
\- JSON 내용을 Binary로 변환하여 패킷용량 감소
- 단점  
\- 아직 JSON이나 XML만큼의 다양한 언어 LIB는 지원하지 않음

##### MSGPACK
- 장점  
\- JSON보다 훨씬 빠른 속도(BJON비교자료는 없지만 보다 빠름)  
\- 자유로운 DTO 전환  
\- 커넥션 풀 지원으로 단순 메시지 서버 구현 가능
- 단점  
\- ANDROID로하기엔 Jboss netty, SLF4J가 포함되어야 하므로 단말기는 반드시 LIB를 로드해야 함  
\- iOS의 Object C는 아직 지원하지 않아 C LIB를 사용해야 함  
\- WEB과 연계가 필요하다면 SESSION에 들어갈 정보에 대한 정리가 필요 함   
