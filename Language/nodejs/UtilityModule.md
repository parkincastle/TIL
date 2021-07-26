## utility 모듈

utility 보듈은 node.js의 보조적인 기능 중 유용한 기능만을 모아놓은 모듈이다.

 - util.format(format, [...]) : console.log() 메소드와 비슷한 기능이지만 console.log()는 화면에 출력하고 util.format은 문자열로 반환한다. printf와 같은 형식으로 첫 아규먼트를 사용해서 포맷팅된 문자열을 반환한다. 플레이스 홀더는 다음과 같은 아규먼트의 값으로 대체된다.

    * %s : 문자열
    * %d : 숫자(정수부터 소수까지 표현 가능)
    * %j : JSON
    * % : 퍼센트 기호('%'). 이 기호는 플레이스홀더를 사용하지 않는다.
  
 - util.debug(string) : 프로그램의 실행을 멈추고 즉각적으로 string을 출력한다.
 - util.log(string) : 타임스탬프 시간과 함께 string을 출력한다.
 - util.isArray(object) : 주어진 object가 Array이면 true, 아니면 false를 리턴한다.
 - util.isRegExp(object) : 주어진 object가 RegExp이면 true, 아니면 false를 리턴한다.
 - util.isDate(object) : 주어진 object가 Date이면 true, 아니면 false를 리턴한다.
 - util.isError(object) : 주어진 object가 Error이면 true, 아니면 false를 리턴한다.

<br>

```JavaScript
var util = require('util');
var data = util.format('%d, %s, %j', 6, 'chapter', {cotent: 'module'});

console.log(data);
util.log('message');
```
