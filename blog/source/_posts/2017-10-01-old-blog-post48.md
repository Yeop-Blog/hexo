---
title: 이클립스 Eclipse Decompiler(JadClipse) 설치
thumbnail: /images/ide_thumbnail.jpg
date: 2017-10-01 17:11:00
categories:
- Programming
- IDE's
tags:
---
- 출처 : http://sooin01.tistory.com/44


1. jad.exe 다운로드  
http://www.varaneckas.com/jad

2. net.sf.jadclipse_x.x.x.jar (현재 3.3.0 버전이 최신)  
http://sourceforge.net/projects/jadclipse/

3. ..\eclipse\plugins 폴더 안으로  
net.sf.jadclipse_3.3.0.jar 파일을 복사 시킨후에 이클립스 다시 껐다가 실행한다.

4. jad 설정  
Window - Preferences - Java - JadClipse 클릭  
{% img 1.jpg /images/post_images/old-blog-post48-1.jpg 첫번째 이미지 %}  
만약에 Path to decompiler 설정에서 Path에 jad.exe가 잡혀있다면 jad만 쓰면 되지만 그렇지 않은 경우에는 jad.exe 파일이 있는 절대경로를 위와 같이 써줘야 한다.

5. Apply -> OK를 하고 .class파일을 보게 되면 이클립스내에서 .class파일을 확인할 수 있다.

6. 추가  
이클립스 설정은 workspace(소스폴더) 안에 .metadata 이 폴더에 저장되어진다.  
나중에 이클립스가 버전업되서 이클립스만 바꾸게 되면 jad가 작동안 할 수도 있다.

원인은 결국 못찾았고 새로운 workspace를 생성하여 설정다시 해주면 잘 된다.
