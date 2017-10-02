---
title: Form에서 CheckBox 배열 하나로 다중 input 값 선택적 전송하기
thumbnail: /images/lang_thumbnail.jpg
date: 2017-10-02 14:07:37
categories:
- Language
- HTML
tags:
---
- 출처 : http://lab.sjworks.net/244

form 태그에서 CheckBox를 배열로 사용해서 다음과 같이 작성해서
~~~html
<form id="form1" name="form1" method="post" action="">
<input type="checkbox" name="chk[]" value="aaa" />
<input type="checkbox" name="chk[]" value="bbb" />
<input type="checkbox" name="chk[]" value="ccc" />
<input type="checkbox" name="chk[]" value="ddd" />
</form>
~~~
두번째와 네번째 체크박스를 선택하고 전송하게 되면 다음과 같이 값이 넘어가게 된다.
~~~
[chk] => Array
(
[0] => bbb
[1] => ddd
)
~~~
그런데 경우에 따라 체크박스의 체크에 따라 다른 input의 값도 선택적으로 보낼 필요가 있다.  
이런 경우 자바스크립트로 간단히 해결할 수 있다.

HTML태그와 자바스크립트 작성 예
~~~html
<form id="form1" name="form1" method="post" action="" onsubmit="_submit(this);">
<!-- row 1 -->
<input type="checkbox" name="chk[]" value="aaa" />
<input type="hidden" name="field_a[]" value="111" />
<input type="hidden" name="field_b[]" value="가가가" />
<!-- row 2 -->
<input type="checkbox" name="chk[]" value="bbb" />
<input type="hidden" name="field_a[]" value="222" />
<input type="hidden" name="field_b[]" value="나나나" />
<!-- row 3 -->
<input type="checkbox" name="chk[]" value="ccc" />
<input type="hidden" name="field_a[]" value="333" />
<input type="hidden" name="field_b[]" value="다다다" />
<!-- row 4 -->
<input type="checkbox" name="chk[]" value="ddd" />
<input type="hidden" name="field_a[]" value="444" />
<input type="hidden" name="field_b[]" value="라라라" />

<input type="submit" name="Submit" id="button" value="Submit" />
</form>

<!-- ... -->

<script language='JavaScript'>
function _submit(f)
{
    //같이 보낼 값 정리
    if (typeof(f.elements['chk[]'].length) == 'undefined') //단일
    {
        if (f.elements['chk[]'].checked==false)
        {
            f.elements['field_a[]'].disabled=true;
            f.elements['field_b[]'].disabled=true;
        }
    } else { //다중
        for (i=0; i<f.elements['chk[]'].length; i++)
        {
            if (f.elements['chk[]'][i].checked==false)
            {
                f.elements['field_a[]'][i].disabled=true;
                f.elements['field_b[]'][i].disabled=true;
            }
        }
    }
    return true;
}
</script>
~~~
각 열마다 chk라는 체크박스와 그에 따른 값 field_a와 filed_b가 있다.
chk[0] 체크박스의 체크 박스에 따라 field_a[0]과 field_b[0]의 전송 여부가 결정되게 하고자 한다.  
form태그에 onsubmit 속성을 써주어 전송될때 이벤트를 자바스크립트 함수 \_submit 으로 추가 처리하도록 했다.  
**자바스크립트로 chk를 하나씩 반복하며 체크가 안되어있는 열은 input함수에 disabled 속성을 추가해줘 전송하지 않도록 한다.**  
이때 주의해야할점은 위 예제의 경우는 chk[]의 수가 일정하지만 php등으로 페이지를 가공할때를 대비하여 chk[]가 하나일경우를 위해 단일과 다중 부분을 나눠서 코딩해야 한다.

이렇게 작성하고 역시 두번째와 네번째를 선택후 전송하면
~~~
[chk] => Array
(
[0] => bbb
[1] => ddd
)
[field_a] => Array
(
[0] => 222
[1] => 4444
)
[field_b] => Array
(
[0] => 나나나
[1] => 라라라
)
~~~
위와같이 전송 되게 된다.
