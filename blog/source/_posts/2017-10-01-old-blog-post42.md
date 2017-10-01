---
title: 자바스크립트의 클로저 (JavaScript's Closure)
thumbnail: /images/javascript_thumbnail.jpg
date: 2017-10-01 16:14:00
categories:
- Language
- JavaScript
tags:
---
- 출처 : http://blog.javarouka.me/2012/01/javascripts-closure.html

자바스크립트를 조금 공부하다보면 바로 맞딱뜨리는 개념중 하나가 클로저 (Closure)라는 개념입니다.  
클로저는 하늘에서 뚝 떨어진 용어도 아니고 프로그래밍 언어에 있는 용어중 하나로서, 언어마다 조금씩 다른 구현과 특성을 가지고 있는 재미있는 개념이죠.  
최근엔 자바 7에도 클로저가 추가되었다고 들었네요.

클로저에 대해 간단히 먼저 정의부터 내려보면, 일종의 어휘적 유효범위(lexical scope)라고 할 수 있는데요.

- **코드가 쓰여진 그 상황에 대한 유효범위를 가지는 코드 블록.**
- **처음 정의되는 시점에서 볼 수 있는 변수들을 실행 위치가 바뀌어도 참조가능.**
- **생성 당시의 환경을 간직한 있는 코드 블록.**
- **자신을 생성해준 객체의 변수 유효범위를 사용할 수 있는 코드 블록.**

글로 쓰게 되니 더욱 어렵습니다.  
위 문장들은 결과적으로는 다 같은 뜻입니다.

그럼 예제 코드를 보죠.  
클로저의 예를 들때 많이 예시가 되는 시퀀스 함수입니다.

~~~javascript
var sequencer = function() {
    var s = 0;
    return function() {
        return ++s;
    }
};

/*
seq 함수는 이런 구조를 가지고 반환될 것입니다
function seq() {
    return ++s;
}
*/
var seq = sequencer();

seq(); // 1
seq(); // 2
seq(); // 3
~~~

보통의 언어라면 말도 안되는 코드입니다.  
이미 sequencer 내부의 s 변수는 다른 언어로 치면 유효범위를 벗어난 쓸 수 없는 변수입니다. 자바같은 가비지 컬렉터를 가진 언어에서는 바로 가비지 컬렉팅의 대상이 되겠지요.

그러나 자바스크립트에서는 다릅니다.

내부 함수는 자신이 선언된 환경에 대해 연결을 갖습니다.  
그래서 위 예제에서 반환된 함수는 자신이 선언될 때의 환경인 sequencer 의 유효범위에 대한 연결을 갖게 되며, 호출하게 되면 그 연결을 통해 s 변수에 **"직접"** 접근합니다.

여기서!!!  
변수를 절대 복사하는게 아님을 유의하세요.  
변수가 있는 객체( - Variable Object 라고 부릅니다)를 참조하는 것입니다.

만일 s 변수를 복사했다면 반환되는 값은 항상 1이어야할 것입니다.  
복사된 변수는 0일테고, 그것에 대해 1이 증가한 값을 반환할 테니까요.

잘 이해가 안되시면 클로저 설명시 자주 언급되는 함수 그 두번째인 클릭시 자신의 순서를 반환하는 핸들러를 붙이는 예제를 봅시다.

~~~javascript
// 모든 LI 태그를 가져와서,
// 클릭시 자신의 순번을 표시하는 예제(?)
var items = document.getElementsByTagName("li");
for(var i=0; i < items.length; i++) {
    items[i].onclick = function(event) {
        alert("My Sequence is " + (i+1)); // 자신의 순번 출력
    }
}
~~~

여기서 프로그래머가 기대한 값은 ``<LI>``태그를 클릭할 때 자신이 문서에 사용된 순서를 출력하는 것일 겁니다. 그러나 여기서 출력하는 값은 LI의 제일 제일 마지막 순번의 값에 1을 더한 값만이 출력됩니다.

만일 문서의 LI 태그가 4개라면 5만을 출력할 것입니다.

값이 복사된 것이 아닌 **변수에 직접 접근** 하고 있기 때문입니다.  
for문이 종료되는 시점의 i값은 4이며, 핸들러들은 그것에 직접 접근하여 1을 더한 값만을 출력하게 되는 것이죠.

위의 함수가 제대로 동작하도록 고쳐봅시다.

~~~javascript
var items = document.getElementsByTagName("li");
for(var i=0; i < items.length; i++) {    
    (function() {   // 새로운 스코프 선언
        var idx = i; // 클로저가 접근할 변수 선언
        items[i].onclick = function(event) {
            alert("My Sequence is " + (idx+1));
        }
    })();
}
~~~

이렇게 고쳐 쓰면 원하는대로 동작합니다.  
이벤트 함수인 클로저가 참조하는 대상이 i가 아닌 새로운 스코프의 idx가 되었기 때문이죠.  
(어렵게 말한다면, 실행 컨텍스트의 스코프 체인 탐색 방법에 따라 참조 순위에서 변수 i는 뒤로 밀립니다)

익명 함수를 쓰는게 좀 어색해 보일 수 있겠지만 자바스크립트에서는 저것이 명시적으로 블럭 스코프를 선언하는 방법입니다.

클로저가 막강한 문법이긴 하나, 주의할 점이 있습니다.  
함수가 메서드로 호출될 때, 외부 함수의 특수한 변수들인 **this**와 **arguments**에는 정상적인 접근이 되지 않습니다.  
정확히는 접근이 되나 저 둘에 대해서는 메서드를 소유한 객체의 **this** 에 연결되지 못합니다.

아래 코드를 봅시다.

~~~javascript
window.name = "window";
var object = {
    name: "object",
    getName: function() {
        function findName() {
            return "my name is " + this.name;
        }
        return findName();
    }
}
object.getName(); // my name is window.
~~~

위의 코드는 의도와는 다른 동작을 보입니다.  
<span style='color: red; font-weight: bold;'>my name is object</span> 가 아닌 <span style='color: red; font-weight: bold;'>my name is window</span> 가 출력됩니다.

메서드 내부의 함수가 실행될 때 this가 메서드를 소유한 객체에 연결된 것이 아닌, 글로벌 객체에 연결되었기 때문입니다. 난감한 결과입니다.

더글라스 크락포드는 이러한 동작을 보고 아래처럼 한마디 했죠.

>이건 명백히 설계상의 실수라고 할 수 있습니다.  
 \- 더글라스 크락포드

내부 함수가 외부 함수를 돕지 못하다니...  
하지만 걱정하지 않아도 됩니다. 보통 이런 경우 관습적으로 사용하는 용법이 있습니다.

~~~javascript
// 위 코드에서 getName 부분입니다
getName: function() {
    var that = this; // this를 따로 변수에 할당해둬 내부 함수가 접근 가능하도록 한다.
    function findName() {
        return "my name is " + that.name;
    }
    return findName();
}
~~~

이렇게 this를 따로 변수에 할당해 두는 방법입니다.  
이렇게 하면 자신의 이름이 잘 출력됩니다.

여기까지 읽고 머리가 좋으시거나, 자바스크립트의 스코프에 잘 이해하고 계신 분이라면 한가지를 알 수 있을거라 생각합니다.

그렇습니다.

**자바스크립트의 모든 함수는 클로저입니다.**

클로저를 잘 익히고 사용할 줄 알아야 자바스크립트를 좀더 유연하게 다룰 수 있습니다.  
언어적 특성을 잘 이해하고 다룰 수 있으면 자바스크립트 코딩이 더욱 재미있어질 거라고 생각합니다.

...  
...  
...  

이대로 끝내긴 좀 아쉬우니 클로저에 대해 한마디 덧붙입니다.  
클로저는 이러한 유연성과 활용의 유연성 등 많은 강점을 가지고 있지만, 그것에 가려진 안좋은 점도 상당합니다.

클로저의 안좋은 점에 대해서는 [다음 포스팅](http://blog.javarouka.me/2012/01/closure.html)에 하도록 해보겠습니다.
