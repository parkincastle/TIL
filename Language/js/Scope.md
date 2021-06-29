# 유효 범위(Scope)란?
<br>

scope의 사전적인 의미는 **범위** 이다. (따라서 스코프를 유효 범위라고 부르기도 한다.)
자바스크립트에서 스코프란 작성된 코드를 둘러싼 환경으로, 어떤 변수들에 접근할 수 있는지를 정의한다.스코프는 **전역(global)** 과 **지역(local)** 스코프로 정의할 수 있다.

<br>

**전역 스코프**는 함수 안에 포함되지 않은 곳에 정의하는 것으로 코드 어디에서든지 참조할 수 있고, **지역 스코프**는 함수 내에 정의된 것으로 정의된 함수 내에서만 참조할 수 있다. 이 개념은 다른 프로그래밍 언어를 공부 했을때 전역변수와 지역변수와 정의와 비슷하다고 볼 수 있습니다. 하지만 자바스크립트의 스코프는 다른 언어와 다른 특징을 가지고 있는데, 바로 자바스크립트는 **함수 레벨 스코프(Function-level scope)** 를 사용한다는 것이다.

```javascript
function foo() {
    if (true) {
        var a = 0; 
        console.log(a);
    }
    console.log(a); 
}
```

<br><br>

# 전역 스코프(Global scope)

<br>

전역에 변수를 선언하면 이 변수는 어디서든지 참조할 수 있는 전역 스코프를 갖는 전역 변수가 된다. **var 키워드로 선언한 전역 변수는 전역 객체(Global Object)** 이다.
<br>

## 전역 스코프의 문제점
 - 변수 이름 중복의 위험성
 - 의도치 않은 재할당에 의한 상태 변화로 코드를 예측하기 어렵게 만든다.

<br><br>

# 지역 스코프(Local scope)

<br>

지역 스코프는 함수 내의 범위로, 각각의 함수마다 자신의 지역 스코프를 가지고 있다.
어떤 함수 내의 지역 스코프에 선언된 변수가 있다면, 그 함수를 벗어난 범위에서는 그 변수를 참조할 수 없다. 따라서 당연하게도, 각각 선언된 함수가 있다면 서로의 스코프에 있는 변수는 참조할 수 없다.

<br>

```javascript
var global_scope = 'global';  // 전역 스코프

var local_function = function() {
    var local_scope = 'insung';  // 지역 스코프
    console.log(global_scope);  // 전역 스코프 참조 가능. global 출력
    console.log(local_scope);  // 함수 내이기 때문에 지역 스코프 참조 가능. goorm 출력
};

console.log(local_scope);  // name은 지역스코프이기 때문에 에러 발생.
```

<br><br>

# 유효 범위 체인(Scope Chain)

<br>

아래 코드와 같이 함수를 정의하면, 제일 안쪽의 함수인 inner는 그 위쪽의 범위까지 흡수하게 됩니다. 이러한 메커니즘을 **유효 범위 체인(Scope Chain)** 이라고 한다.

<br>

외부에서는 안에 있는 함수의 변수를 참조할 수 없지만, 안에 있는 함수에서는 외부의 변수를 사용할 수 있다.

<br>

```javascript
var a = 1;

function outer() {
	var b = 2;
	console.log(a);
	
	function inner() {
		var c = 3;
		console.log(b);
		console.log(a); 
	}
	
	inner();    // 2 1
}
outer();

console.log(c); //  c is not defined

```

<br>

> a는 전역공간에서 선언되었기 때문에 함수 inner와 outer에서 사용할 수 있지만, 변수 c는 함수 내부 블록에서 선언되었기 때문에 함수의 밖인 전역범위에서는 인식하지 못한다. 그리고 outer에서도 c는 사용할 수 없지만 inner함수 안에서는 상위 스코프인 변수 a, b 모두 사용할 수 있다.

# 정적 범위(Lexical scope)
**렉시컬 스코프는 함수를 어떤 스코프에 선언하였는지에 따라 결정된다.** 자바스크립트는 렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정된다. 함수를 어디에서 호출하였는지는 스코프 결정에 아무런 의미를 주지 않는다.

```javascript
var text = 'global';

function foo() {
	console.log(text);
}

function bar() {
	var text = 'bar';
	foo();
}

bar(); // global
```
foo에서 출력한 text는 bar 함수의 지역 변수 text가 아니라 전역변수 text를 가르키고 있기 때문에 global이 출력된다. 이건 위에 설명한 스코프 체인과 관련이 있는 개념인데 foo함수는 bar에서 호출되든 어떤 함수 안에서 호출되던지 상관없이, 무조건 자기 자신의 스코프를 찾아보고 그 이후에는 전역 스코프를 찾는다.

만약 text를 bar로 바꾼후 출력하고 싶다면 지역변수 var를 선언할 것이 아니라 전역변수 var의 값을 바꾸면 된다.

```javascript
var text = 'global';

function foo() {
	console.log(text);
}

function bar() {
    text = 'bar';
	foo();
}

bar(); // bar
```

