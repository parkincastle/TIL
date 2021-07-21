## 전역 객체 (Global)

앞서 말했듯이 전역 객체는 어디에서나 사용할 수 있는 객체이다. 그 중 Node.js에서 가장 많이 쓰이는 전역 객체에 대해서 세부적으로 살펴보자.

### console 객체

콘솔화면과 관련된 기능을 갖고 있다. 여러 가지 메소드가 있지만 log를 제외하면 잘 쓰이지 않는다.

 - console.log() : 콘솔에 로그 메시지 출력
 - console.time(label) : 시간 측정
 - console.timeEnd(label) : 시간 측정 종료

log로 출력 시 지정한 포맷보다 변수가 많으면 그대로 출력하고 부족하다면 특수 문자를 출력한다.

```JavaScript
console.log('%d + %d = %d', 1, 2, 1+2);
    > 1 + 2 = 3
console.log('%d + %d = %d', 1, 2, 1+2, 4);
    > 1 + 2 = 3 4
console.log('%d + %d = %d', 1, 2 );
    > 1 + 2 = %d

```

<br><br>

## Process 객체

프로그램과 관련된 기능을 다루는 객체이다. process 개체는 자바스크립트에는 없는, Node.js만의 객체이다. 

속성과 메소드가 많은 편이다.


**속성**
 - process.argv : 프로그램의 매개변수 정보
 - process.env : 컴퓨터 환경과 관련된 정보
 - process.version : Node.js의 버전
 - process.versions : Node.js 프로세스에서 사용하는 모듈들의 버전
 - process.arch : 프로세서의 아키텍처
 - process.platform : 플랫폼의 정보


**메소드**
 - process.exit() : 프로그램 종료
 - process.memoryUsage() : 메모리 사용 정보
 - process.uptime() : 현재 프로그램이 실행된 시간


## Exports 객체

모듈 관련 객체로, Node.js는 Exprots 객체를 사용하여 기능을 확장할 수 있다. 모듈은 기능을 쉽게 사용하기 위해 메소드와 속성을 밀 정의해서 모아 놓은 것이다.

모듈을 생성하려면 파일을 만들고, exports객체의 속성이나 메소드로 정의 해준면 된다. 만들어진 모듈은 전역함수 requite()을 이용하여 추출한다.

<br><br>

## OS 모듈
OS모둘은 실제 개발에서 많이 사용되는 모듈은 아니지만 윤영체제와 시스템의 정보를 가져올 수 있는 모듈이다. CPU나 메모리, 디스크 용량이 얼마나 남았는지 확인이 필요할 때 사용된다.
<br>

 - os.tmpdir() : 임시 저장 폴더의 위치
 - os.endianness() : CPU의 endianness(BE 또는 LE)
 - os.hostname() : 호스트(컴퓨터) 이름
 - os.type() : 운영체제 이름
 - os.platform() : 운영체제 플랫폼
 - os.arch() : 운영체제 아키텍처
 - os.realease() : 운영체제 버전
 - os.uptime() : 운영체제가 실행된 시간
 - os.loadavg() : 시스템의 총 메모리
 - os.totalmem() : 시스템의 총 메모리
 - os.freemem() : 시스템의 가용 메모리
 - os.cpus() : CPU의 정보를 담은 객체, CPU의 세부 정보를 반환한다.
 - os.networkinterfaces() : 네트워크 인터페이스 정보를 담은 배열

<br><br>

**os 객체의 유일한 속성**
 - os.EOL : 운영체제의 개행 문자(\n과 같은 문자)

require()함수를 통해 직접 선언해준 후 그 변수를 이용해 사용해야 합니다. 모듈들을 어떻게 가져오고 상요하는지 예제를 통해 알아봅시다. 프로세스 객체와 마판가지로, 위의 값들이 어떻게 나오는지 직접 확인해보고 싶다면 console.log를 이용해 집접 확인해보세요. 

단, cpus() 메소드는 CPU의 개수만큼 배열로 반환하기 때문에 주의해야 한다. 나머지 메소드나 속성은 문자열이나 숫자 형태로 반환하므로 쉽게 사용할 수 있다.

<br>

```JavaScript
var os = require('os');

console.log(os.tmpdir());
console.log(os.type());

var cpus = os.cpus();

for(var i = 0; i < cpus.length; i++) {
	console.log("CPU[" + (i+1) + "]");
	console.log("model: " + cpus[i].model);
	console.log("speed: " + cpus[i].speed);
}
```

<br><br>

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

<br><br>

## FIle System 모듈

노드에서 가장 중요한 모듈로 파일 처리와 관련된 작업을 한다, 보통 FileSystem을 줄여서 fs 모듈이라고 불린다. 

메소드가 매우 많아서 기초인 파일 읽기와 쓰기기능을 살펴보겠다.

대부분의 메소드들이 동기/비동기로 나뉘는데, Sync라는 이름이 붙어있는 메소드가 동기방식을 사용한다고 보면 된다.

**동기적 읽기 방식**을 사용하면 파일을 읽으면서 다른 작업을 동시에 할 수 없다.

하지만 **비동기적**으로 읽으면 차일을 읽으면서 다른 작업도 동시에 수행할 수 있고 차일을 다 읽으면 애개변수 callback으로 전달한 함수가 호출된다.
비동기 형신은 항상 마지막 인수가 수행 완료 시 호출할 콜백 함수로 적성되어야 한다.

주로 비동기적 형식을 많이 사용하지만 , 서버 시작 시 설정 파일을 읽는 작업과 같이 동기적 형식이 더 적절한 경우도 있다.

 - fs.readFile(filename, [options], callback) : filename의 파일을 [options]의 방식으로 읽은 후 callback으로 전달된 함수를 호출한다. (비동기적) 
 - fs.readFileSync(filename, [options]) : filename의 파일을 [options]의 방식으로 읽은 후 문자열을 반환한다.(동기적)
 - fs.writeFile(filename, data, [options], callback) : filename의 파일에 [options]의 방식으로 data 내용을 쓴 후 callback 함수를 호출한다.(비동기적) 
 - fs.writeFileSync(filename, data, [options]) : filename의 파일에 [options]의 방식으로 data 내용을 쓴다.(동기적)




