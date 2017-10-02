---
title: HTML for문 안에서 radio버튼 사용시 name이 같을 경우 해결책
thumbnail: /images/lang_thumbnail.jpg
date: 2017-10-02 11:45:05
categories:
- Language
- HTML
tags:
---
for문 안에서 radio버튼 사용시 name이 같으면 for문이 아무리 돌아도 radio버튼이 하나만 체크가 되어 나온다.  
그럴 경우에는 radio버튼에 해당하는 name값을 for문이 돌 때 마다 각기 다르게 들어가게 해준다.  
ex) ``type="radio" name="tests[${i.index}]"``  
위와 같이 되면 test0, test1, test2 이런식으로 name값이 정해진다.  
여기서 중요한 점은 radio에 해당하는 값을 받는 변수는 List나 배열로 선언을 해주고 사용을 해야 한다.  
ex) ``ArrayList<String> tests 또는 String[] tests``  
그렇게 List나 배열로 선언을 해주고 컨트롤단에서 제대로 값을 받는지 확인을 한 후 제대로 들어온다면 List나 배열에서 실제 그 값을 활용하는 곳에다가 for문을 돌리면서 값을 꺼내서 셋팅을 해준다.   
~~~html
ex) for(int i = 0; i<tests.size(); i++){
      test.set(tests.get(i));
    }
~~~
\* **결론 : name이 같으면 제대로 radio값을 입력할 수 없으므로 변수명을 달리해서 List나 배열로 받아 처리한다.**
