---
title: Javascript Opener클래스를 통해 자식창에서 부모창의 객체에 접근및 제어하는 예제
categories:
- Language
- JavaScript
tags:
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-09-20 23:43:29
---
밑의 domodal형의 예제처럼 자식창의 리턴값을 부모에서 받아서 사용할수도 있지만,  
자식창에서 일방적으로 부모창의 객체에 접근하여 값을 입력할수도 있습니다.  
이때 사용되는 코드가 opener클래스입니다.

예제는 부모창은 자식창을 호출하는 기능,  
자식창은 부모창의 input:text에 값을 넣고 종료되는 기능으로 구현해봤습니다.

#### 부모창 코드  
```html
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title></title>
</head>
<body>
    <script type="text/javascript">
        function goChild() {
            window.open("Child.htm");
        }
    </script>

    <input id="btn" type="button" value="자식창열기" onclick="goChild()" />
    <input id="txt" type="text" value="여기에 자식창이 보낸 정보를 받는다." style="width:100%;" />
</body>
</html>
```
#### 자식창 코드
```html
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <title></title>
</head>
<body>
    <h1>자식창</h1>
    <input id="Text1" type="text" /><input id="Button1" type="button" value="부모창에 왼쪽텍스트박스의 정보 보내는 버튼" onclick="goParent()" />
    <script type="text/javascript">
        function goParent() {
            opener.document.getElementById("txt").value = document.getElementById("Text1").value;           
            window.close();
        }
    </script>
</body>
</html>
```
