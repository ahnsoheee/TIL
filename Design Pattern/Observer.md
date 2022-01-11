## 관찰자 패턴 (Observer Pattern) 

- 상태 변화가 일어날 때 관찰자(또는 listener)에게 알릴 수 있는 객체(Subject)를 정의하는 것
- 객체의 상태 변화가 있을 때마다 옵저버에게 통지하도록 하는 디자인 패턴
- 발행/구독 모델

### 관찰자 패턴 vs 콜백 패턴
- 관찰자 패턴 : Subject가 실제로 여러 관찰자(Observer)들에게 알릴 수 있다.
- 콜백 패턴 : 일반적으로 그 결과를 하나의 listener인 콜백에만 전파한다.

### Node.js - EventEmitter 클래스
#### 필수 메소드
- on(event, listener) : 주어진 이벤트 유형(문자열)에 대해 새로운 리스너를 등록할 수 있다.
- once(event, listener) : 첫 이벤트가 전달된 후 제거되는 새로운 리스너를 등록한다.
- emit(event, [arg1], [...]) : 새 이벤트를 발생시키고 리스터에게 전달할 추가적인 인자들을 지원한다.
- removeListener(event, listener) : 지정된 이벤트 유형에 대한 리스너를 제거한다.

```js
const EventEmitter = require('events').EventEmitter;
const fs = require('fs');

function findPattern(files, regex) {
    const emitter = new EventEmitter();
    files.forEach(function(file) {
        fs.readFile(file, 'utf8', (err, content) => {
            if (err) return emitter.emit('error', err);

            emitter.emit('fileread', file);
            let match;
            if (match = content.match(regex))
                match.forEach(elem => emitter.emit('found', file, elem));
        });
    });
    return emitter;
}


<details>
<summary>참고</summary>

- Node.js 디자인패턴


</details>