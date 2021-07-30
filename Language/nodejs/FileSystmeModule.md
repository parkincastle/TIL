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


<br>

### readfile 예제

<br>

```JavaScript
//main.js
var fs = require('fs');
 

// 비동기적 읽기
fs.readFile('text.txt', 'utf8', function(err, data) {
    console.log('비동기적 읽기 ' + data);
});

// 동기적 읽기
var text = fs.readFileSync('text.txt', 'utf8');
console.log('동기적 읽기 ' + text);
```

위 코드는 비동기적 읽기가 먼저 실행됨에도 불구하고 console에는 동기적 읽기가 먼저 출력됨을 볼 수 있다. 쓰기도 마찬가지로 아래 코드를 실행하면 동기적 쓰기 완료가 먼저 출력된다.

<br>

### writefile 예제

<br>

```JavaScript
// main.js
var fs = require('fs');
 
var data = 'fs.writeFile test';
 
fs.writeFile('text1.txt', data, 'utf8', function(err) {
    console.log('비동기적 파일 쓰기 완료');
});
 
 
fs.writeFileSync('text2.txt', data, 'utf8');
console.log('동기적 파일 쓰기 완료');
```

파일 입출력은 다양한 원인으로 예외가 발생할 수 있으므로 파일 입출력을 하면서 중요한 부분 중 하나가 예외처리이다. 시스템이 비정상적으로 종료되지 않게 하기 위한 필수 사항이데, 동기적 방식과 비동기적 방식에서 예외처리의 방식이 조금씩 다르게 되어있다.

<br>

### 동기적 방식 예외처리 

<br>

```JavaScript
// main.js
var fs = require('fs');
 
// 파일 읽기(동기적)
try {
	var data = fs.readFileSync('notexist.txt', 'utf8'); // 파일이 없는데 읽으려 함
	console.log(data);
} catch (err) {
    console.log(err);
}
```

동기적 방식에서 자바스크립트 예외처리를 할 때 일반적으로 써주는 방식인 try-catch 구문으로 처리한다. 

<br>

### 비동기적 방식 예외처리

<br>

```JavaScript
// main.js
var fs = require('fs');
 
// 파일 읽기
fs.readFile('notexist.txt', 'utf8', function(err, data) { // 존재하지 않는 파일 읽기
    if (err) {
        console.log(err); // 읽기 실패
    }
    else {
        console.log(data); // 읽기 성공
    }
});
```

비동기적 방식에서는 예외가 발생하면 callback 함수의 매개변수 err에 전달되므로, 따로 try-catch구문을 사용할 수 없다.
