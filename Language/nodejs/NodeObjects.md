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
