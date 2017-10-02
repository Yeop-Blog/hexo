---
title: Spring loadUserByUsername 메소드 수정시 주의할 점
thumbnail: /images/framework_thumbnail.jpg
date: 2017-10-02 14:17:54
categories:
- Framework
- Spring
tags:
---
loadUserByUsername를 다시 꺼내서 사용할 시 주의할 점은  
해당 메소드를 쓰는 ServiceImpl의 어노테이션 부분이 xml에 설정되어 있는지 확인이 필요.  
ex) ``@Service ("UXMemberService")``라고 어노테이션을 선언한 ServiceImpl에 사용한다면  
context-security.xml 또는 security-context.xml 부분에서 선언이 되어 있는
~~~
<sec:authentication-manager alias="authenticationManager">
 <sec:authentication-provider user-service-ref="UXMemberService">
  <sec:password-encoder ref="UIPasswordEncoder">
 </sec:password-encoder></sec:authentication-provider>
</sec:authentication-manager>
~~~
위 부분에서 ``authentication-provider user-service-ref`` 명이 UXMemberSerivce로  
어노테이션 명칭과 일치해야 정상적으로 내가 설정해서 사용하는 loadUserByUsername메소드를 타고 들어간다.
