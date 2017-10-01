---
title: 이클립스 Properties Editor 한글 사용 (eclipse 3.7.2)
thumbnail: /images/ide_thumbnail.jpg
date: 2017-10-01 16:26:00
categories:
- Programming
- IDE's
tags:
---
- 출처 : http://kdarkdev.tistory.com/37

이클립스의 기본 Properties Editor는 한글로 바로 표현이 안되고 유니코드로 표현되므로 유니코드를 한글로 인식시킬수있는 플러그인이 필요합니다.  
테스트는 이클립스 3.7.2에서 했으며 이전에 사용하던 3.4, 3.5에서도 이상없이 동작 했습니다.

1. 이클립스 메뉴의 Help->Install New Software 클릭
2. 상단의 Add버튼 클릭후 Name에는 아무이름이나 정하고 Location에는 http://propedit.sourceforge.jp/eclipse/updates 입력하고 OK 클릭
3. 목록에 Pending이라는 글이 뜨고 잠시 기다리면 저장소에서 검색된 목록이 뜨는데
목록중 가장하단의 PropertiesEditor에 체크하고 next누르고 다음단계에서도 Next누르면서 설치.
4. 만약 이클립스 3.6이상을 사용중이라면 이클립스 marketplace를 이용하면 더 편하게 설치 할 수 있는데
방법은 이 블로그의 http://kdarkdev.tistory.com/36에서 find항목의 검색어만 변경하면 되는데 검색어는 properties editor 이고 세번째에 있는 'Pe' 라는 로고를 가진 플러그인을 선택하면 된다.

\- 설치후 이클립스 재시작 후 에도 Properties Editor가 설정 안될경우  
이클립스 메뉴의 window-preferences-general-Editors-File Associations의 \*.properties 찾아서 하단의 Associated editors에 PropertiesEditor를 default로 설정한다.
