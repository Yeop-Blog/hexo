---
title: 이클립스(Eclipse) HotSwap기능이 있는 JRebel 무료 사용법. (Java단을 Tomcat 재시작 없이 확인 가능)
thumbnail: /images/ide_thumbnail.jpg
date: 2017-10-01 22:03:00
categories:
- Programming
- IDE's
tags:
---
<span style='color: red; font-weight: bold;'>※ 글 작성에 앞서 아래 jRebel은 기업 및 기업에서 개인이 사용시에는 반드시 유료로 구매하셔서 사용하셔야 하는 프로그램임을 먼저 명시하고 알려드립니다.  
이를 무시하고 사용시 당하는 불이익에 대해서는 책임이 없으니 이 점 유념해주시기 바랍니다.</span>

1) 아래 사이트에 접속합니다.  
\- https://my.jrebel.com/

2) 접속하면 아래와 같은 화면이 뜨는데 여기서 회원가입을 우선 해야 합니다.  
\- **여기서 가입은 무조건 SNS계정으로 가입해야 합니다.**  
(SNS 계정을 통해 차후 free결제를 진행해야 하기 때문에 SNS계정이 없는 분은 하나 만들어 두면 여러모로 편합니다~)  
{% img /images/post_images/old-blog-post64-1.png 첫번째 이미지 %}

3) 여기서는 트위터로 진행을 하도록 하겠습니다. (페이스북 사용자 역시 비슷한 과정으로 진행하시면 됩니다) 위 화면에서 Connect w/ Twitter버튼을 클릭하면 아래와 같은 화면이 나오고 해당 화면에서 자신이 만든 계정 혹은 가지고 있는 계정의 이메일주소와 비밀번호를 입력후 애플리케이션 승인 버튼을 누릅니다.  
{% img /images/post_images/old-blog-post64-2.png 두번째 이미지 %}

4) 승인 버튼을 누르고 인증 절차에 따라 진행 된후 아래와 같은 화면이 나오는데 간단하게 자신의 이름과 이메일주소, 직업 등을 입력하는 란입니다. 아래와 같이 간단하게 적어주시고.. SIGN UP 버튼을 클릭해주세요.  
{% img /images/post_images/old-blog-post64-3.png 세번째 이미지 %}

5) SIGN UP 버튼을 누르면 위에서 적은 자신의 이메일 계정으로 승인 메일이 날라오게 됩니다. 혹시나 계속 기다렸는데 안오면 아래 request it again 버튼을 한번 더 눌러주세요. 그렇게 해서 승인 메일이 도착하고 확인해 보면 2번째 화면과 같이 링크 부분이 있습니다. 그 부분을 클릭 또는 클릭이 안되면 복사후 인터넷 주소창에 붙여넣고 엔터를 쳐주세요.  
{% img /images/post_images/old-blog-post64-4.png 네번째 이미지 %}  
{% img /images/post_images/old-blog-post64-5.png 다섯번째 이미지 %}

6) 제대로 인증이 되었다면 아래와 같은 화면이 나옵니다. 여기서 Social 부분의 SUBSCRIBE 버튼을 클릭.  
{% img /images/post_images/old-blog-post64-6.png 여섯번째 이미지 %}

7) 클릭하시면 Social Plan이라는 화면과 함께 아래와 같은 화면이 나오는데 여기서 자신이 만든 SNS계정에 속하는 부분의 Click here라고 표시된 부분을 클릭하면 됩니다.  
{% img /images/post_images/old-blog-post64-7.png 일곱번째 이미지 %}

8) 클릭하면 아래와 같은 화면이 나오고 여기서 승인 버튼 클릭.  
{% img /images/post_images/old-blog-post64-8.png 여덟번째 이미지 %}

9) 인증 절차후 다시 아래와 같은 화면이 나오면 SUBSCRIBE 클릭.  
{% img /images/post_images/old-blog-post64-9.png 아홉번째 이미지 %}

10) 보시면 0$ 결제 보이실겁니다. 그 아래 간단한 연락처 기재 부분이 있는데 적당히 적고 COMPLETE ORDER 클릭.  
{% img /images/post_images/old-blog-post64-10.png 열번째 이미지 %}

11) 클릭하셔서 여기까지 나오시면 우선 jRebel 구매는 완료가 되신겁니다. 이제 자신이 쓰는 IDE에 jRebel설치 후 라이센스 코드를 입력하여 사용하면 끝입니다. IDE설치부터 jRebel Activate License사용까지에 대해서는 타 블로그에서 자세히 설명된 부분이 있으니 그 블로그 페이지를 참고해주시기 바랍니다. (해당 블로그는 아래 링크를 걸어두겠습니다.)  
{% img /images/post_images/old-blog-post64-11.png 열한번째 이미지 %}

**< jRebel 사용법 및 이클립스 설치 과정에서 라이센스 등록까지.. 참고 블로그 주소들 >**  
\- 보시면 아시겠지만 설치 과정에서 화면이 틀릴 수 있지만 기본적인 내용은 거의 비슷하기 때문에 문제는 없으실거라 생각 됩니다.
저 역시 아래 블로그 참고해서 설치 마무리 한 사람이니깐요 ^^;;

1.이클립스 jRebel 설치 공식 튜토리얼 -  http://zeroturnaround.com/software/jrebel/eclipse-jrebel-tutorial/

2.http://belong2jesus.tistory.com/44  
(개인적으로는 이 블로그를 위주로 참고하여 설치 진행하였습니다.)

3.http://blog.naver.com/PostView.nhn?blogId=rcnboys&logNo=20115400550&parentCategoryNo=44&viewDate=&currentPage=1&listtype=0
