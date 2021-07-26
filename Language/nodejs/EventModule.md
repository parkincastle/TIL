## Event 모듈
노드의 많은 객체는 이벤트를 발생기키는데, 이러한 객페들은 마로events.EventEmmitter라는 인스턴스를 이용하고 있다. 이벤트 이름은 띄어쓰기 대신 대문자로 문자를 구분하는 **카멜 표기법**을 사용하는 것이 정석이지만 강제는 아니다. Node.js에서는 이벤트 모듈과 EventEmitter 클래스가 내장되어 있는데, 이를 사용하여 이벤트와 이벤트핸들러를 연돌시킬 수 있다.

이벤트를 활용하는 객체에는 해당 이벤트가 발생할 깨 대응하여 동작하는 콜백함수를 가지는데, 이러한 함수를 이벤트 리스너라고 하기도 한다. 이벤트 모듈을 사용하여면 require() 메소드를 이용하여 로드하고, 그 객체를 통해 EventEmitter 클래스를 로드하여 사용하는 것이 일반적이다.
   

### events 객체의 메소드
 - emitter.addListener(event, listener) : on()메소드와 같다. 이벤트를 생성하는 메소드이다.
 - emitter.on(event, listener) : addListener()과 동일하다. 이벤트를 생성하는 메소드
 - emitter.once(event, listener) : 이벤트를 한 번만 연결한 후 제거한다.
 - emitter.removeListener(event, listener) : 특정 이벤트의 특정 이벤트 핸들러를 제거한다. 이 메소드를 이용해 리스너를 삭제하면 리스너 배여릐 인덱스가 갱신되니 주의
 - emitter.removeAllListeners([events]) : 모든 이벤트 핸들러를 제거한다.
 - emitter.setMaxListeners(n) : n으로 한 이벤트에 최대허용 개수를 정해준다.
  node.js는 기본값으로 한 이벤트에 10개의 이벤트 핸들러를 작성할 수 있다. 11개 이상을 사용하고 싶다면 n값을 넘겨주면된다. n값으로 0을 넘겨 주면 열결 개수 제한이 사라진다.
 - emitter.emit(eventName[, ...args]) : 이벤트를 발생시킨다

## 이벤트 생선(이벤트 핸들러 연결)

이벤트를 추가하려면, emitter에 이벤으를 연결할 객체, event에 이벤트 이름, listener에 이벤트 핸들러를 작성하면 된다(사용할 메소드는 addlistener(), on() 둘 중 익숙한 것을 사용하면 된다.)

```JavaScript
var EventEmitter = require('events');

var custom_event = new EventEmitter();

custom_event.on('call', function() {
	console.log('이벤트 콜');
});

custom_event.emit('call');
```

   
## 이벤트 제거
addlistener() 메소드나 on() 메소드를 통해 연결된 핸들러를 제거하기 위해 사용된다. removeListener()를 사용하면 모든 이벤트 리스너를 제거한다.
removeAllListeners([eventname])을 사용하면 해당 이벤트의 모든 리스너를 제거한 수 있다.

```JavaScript
var EventEmitter = require('events');

var custom_event = new EventEmitter();

custom_event.on('call', function() {
	console.log('이벤트 콜');
});

custom_event.removeAllListeners();

custom_event.emit('call');
```

아까와 거의 비슷한 코드지만, call 이벤트를 부르기 전 리스너를 삭제했기 때문에 콘솔에 아무것도 찍히지 않는다.