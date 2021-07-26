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