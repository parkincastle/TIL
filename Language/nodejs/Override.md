# 노드에서의 상속

노드는 자바스크립트를 기본으로 만들어졌기 때문에 자바스크립트와 동일하게 상속할 수 있지만, 좀 더 편리하게 상속할 수 있도록 util모듈을 통해 별도의 메소드를 지원하고 있다. 먼저 전통적인 자바스크립트 상속 방법을 살표본 후, 노드의 util 모듈에서 지원하는 상속방법을 알아보자


<br><br>

## 자바스크립트에서의 상속 방법

```JavaScript
function Foo() {
    // 코드
}

Foo.prototype = {
    bar: function() {
        console.log('Foo_bar 실행');
    }
};
```

위의 코드는 bar() 메소드를 가진 Foo 객체를 생성하는 코드이다. Foo를 상속받아 Bar 객체를 생성하는 코드를 아래에서 상료보자

```JavaScript
function Bar() {
}

Bar.prototype = Object.create(Foo.prototype);

Bar.prototype.baz = function() {
    console.log('Bar_baz 실행')
}

Foo.prototype.bar();
Bar.prototype.bar();
Bar.prototype.baz();
```

Foo 객체의 원형을 상속받은 Bar 객체는 Foo의 Bar() 메소드를 사용할 수 있게 되었다.

<br><br>

## util.inherits() 메소드를 이용한 상속

하지만, 노드에서 지원되는 util.inherits() 메소드를 이용하면 더 쉽고 간단하게 상쇽할 수 있다. 커다란 차이는 없지만, 작성해야 하는 코드의 양이 조금 줄어들고, Bar이 Foo를 상속받았다는 것을 명확하게 보이게 해준다.

```JavaScript
var util = require('util');

function Bar() {
}

util.inherits(Bar, Foo);

Bar.prototype.baz = function() {
	console.log('Bar_baz 실행');
};

Foo.prototype.bar();
Bar.prototype.bar();
Bar.prototype.baz();
```


