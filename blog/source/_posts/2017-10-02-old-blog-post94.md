---
title: 서버단 패스워드 유효성 검증 로직
thumbnail: /images/java_thumbnail.jpg
date: 2017-10-02 15:01:06
categories:
- Language
- Java
tags:
---
~~~java
/**
 * 패스워드 유효성 검증
 *
 * @param passwd
 * @return
 */
public String passwordValidator(String passwd){
  String returnValue = "success";

  Pattern p = Pattern.compile("([a-zA-Z0-9].*[!,@,#,$,%,^,&,*,?,_,~])|([!,@,#,$,%,^,&,*,?,_,~].*[a-zA-Z0-9])");
  Matcher m = p.matcher(passwd);

  Pattern p2 = Pattern.compile("(\\w)\\1\\1\\1");
  Matcher m2 = p2.matcher(passwd);

  Pattern p3 = Pattern.compile("([\\{\\}\\[\\]\\/?.,;:|\\)*~`!^\\-_+<>@\\#$%&\\\\\\=\\(\\'\\\"])\\1\\1\\1");
  Matcher m3 = p3.matcher(passwd);

  if(spaceCheck(passwd)){	//패스워드 공백 문자열 체크
    returnValue = "비밀번호에 공백문자를 허용하지 않습니다.";
  }else if(passwd.length() < 10 || passwd.length() > 16){	//자릿수 검증
    returnValue = "비밀번호는 10자 이상, 16자 이하로 구성하세요.";
  }else if(!m.find()){	//정규식 이용한 패턴 체크
    returnValue = "비밀번호는 영문,숫자,특수문자(!@$%^&* 만 허용)를\n조합하여 10~16자로 구성하세요.";
  }else if(m2.find() || m3.find()){	// 동일 문자 4번 입력 시 패턴 체크
    returnValue = "비밀번호에 동일문자를 4번 이상 사용할 수 없습니다.";
  }else if(continueNumberCheck(passwd)){	// 비밀번호 연속 숫자 4자리 체크
    returnValue = "비밀번호에 연속된 숫자를 4자 이상 사용 할 수 없습니다.";
  }

  return returnValue;
}

/**
 * 공백 문자 체크
 *
 * @param spaceCheck
 * @return
 */
public boolean spaceCheck(String spaceCheck){
  for(int i = 0 ; i < spaceCheck.length() ; i++) {
    if(spaceCheck.charAt(i) == ' ')
      return true;
  }

  return false;
}

/**
 * 연속된 숫자 체크
 *
 * @param numberCheck
 * @return
 */
public boolean continueNumberCheck(String numberCheck){
  int o = 0;
  int d = 0;
  int p = 0;
  int n = 0;		
  int limit = 4;

  for(int i = 0 ; i < numberCheck.length() ; i++) {
    char tempVal = numberCheck.charAt(i);
    if (i > 0 && (p = o - tempVal) > -2 && p < 2 && (n = p == d ? n + 1 : 0) > limit - 3)
      return true;
    d = p;
    o = tempVal;
  }

  return false;
}
~~~
