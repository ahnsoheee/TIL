## Callback
- 다른 함수에 인수로 전달되는 함수이며, 작업이 완료되면 결과로 호출된다.
- 클로저 : 콜백이 언제 어디서 호출되는 지에 관계없이 비동기 작업이 요청된 컨텍스트를 항상 유지할 수 있다.

### 연속 전달 (CPS: Continuation-Passing Style)
- 함수형 프로그래밍에서 결과를 전달하는 방식
- 결과를 호출자에게 직접 반환하는 대신 콜백으로 전달하는 것

#### 동기식 연속 전달 방식
```js
function add(a, b, callback) {
    callback(a + b);
}

console.log('before');
add(1, 2, result => console.log('result: ' + result));
console.log('after');

// before
// result: 3
// after
```
- add()는 동기화된 CPS 함수로 콜백이 완료될 때만 값을 반환한다.

#### 비동기식 연속 전달 방식
```js
function addtionAsync(a, b, callback) {
    setTimeout(() => callback(a + b), 100);
}

console.log('before');
add(1, 2, result => console.log('result: ' + result));
console.log('after');

// before
// after
// result: 3
```
- setTimeout()은 비동기 작업을 실행시키기 때문에 콜백의 실행이 끝날 때까지 기다리지 않는 대신, 즉시 반환되어 additionAsync()로 제어를 돌려주어 제어가 호출자에게 반환된다. 비동기 요청이 전달된 후 즉시 제어를 이벤트 루프에 돌려주어 큐에 있는 새로운 이벤트 처리가 될 수 있도록 하기 때문이다.
- 비동기 작업이 완료되면 실행은 비동기 함수에 제공된 콜백에서부터 다시 계속된다.
- 클로저로 인해 콜백이 다른 시점과 다른 위치에서 호출되더라도 비동기 함수의 호출자 컨텍스트를 유지한다.

=> 동기 함수는 조작을 완료할 때까지 블록하고, 비동기 함수는 제어를 즉시 반환하고 결과는 이벤트 루프의 다음 사이클에서 핸들러(콜백)로 전달된다.

### 비 연속 전달 (Non-continuation-passing) 
- Array 객체의 map() 함수
```js
const result = [1, 5, 7].map(element => element -1);
console.log(result); // [0, 4, 6]
```
- 콜백은 배열 내의 요소를 반복하는데 사용될 뿐 연산 결과를 전달하지 않는다.

### 동기? 비동기?

#### 동기 API 사용
- 비동기식 코드는 예측할 수 없는 오류가 발생할 수 있다.
- **직접 스타일을 사용해 동기식 API를 구현하는 것이 최선의 방법이다!!**
- 함수가 동기식이면 연속 전달 방식을 가질 필요가 없다.
- 혼란을 제거하고 성능 측면에서 보다 효율적이다.
- 주의할 점 
    - 동기 API는 이벤트 루프를 블록하고 동시 요청을 블록하기 때문에 JS 동시성 모델을 깨뜨려 전체 어프리케이션 속도를 떨어뜨린다.
    - 동기식 I/O API가 큰 파일을 읽는 경우 이벤트 루프를 블로킹하는 것은 큰 영향을 줄 수 있다.
    - 어플리케이션이 부팅되는 동안 동기 차단 API를 사용해 환경 파일들을 로드하는 것이 최적
    - 어플리케이션이 동시 요청을 처리하는데 영향을 주지 않는 경우에만 블로킹 API를 사용하자.

#### 지연 실행
- 완전히 비동기로 만드는 것
- process.nextTick()
    - 이벤트 루프의 다음 사이클까지 함수의 실행을 지연시키는 것
    - 콜백을 인수로 취해 대기중인 이벤트 대기열의 앞으로 밀어 넣고 즉시 반환
- setImmediate()
    - process.nextTick()와 달리 이미 큐에 있는 이벤트들의 뒤에 대기한다.

### 오류
- 어플리케이션은 예외가 이벤트 루프에 도착하는 순간 중단된다.

#### 동기
- 직접 스타일 함수는 throw문을 사용해 수행되기 때문에, 오류가 catch될 때까지 호출 스택에서 실행된다.

#### 비동기
- 비동기식 CPS는 콜백으로 전달해서 수행하고, 에러를 전파할 때 return 문을 사용한다.
- 비동기 콜백 내부에서 예외가 발생하면 예외가 이벤트 루프로 이동해 다음 콜백으로 전파되지 않는다.
- 비동기 함수 실행은 이벤트 루프에 의해 각기 다른 스택에서 실행되기 때문에 트리거 함수가 아닌 이벤트 루프에서 끝난다.

```js
function readJSON('foo.txt' , callback) {
    fs.readFile(filename, (err, data) => {
        if (err) 
            return callback(err)
        callback(null, JSON.parse(data));
    })
})
```
- 위 코드에서 JSON.parse(data) 함수에서 발생하는 예외를 잡지 못한다. 겉에 try...catch 사용해도 예외가 발생한 스택과 실행 스택이 다르기 대문에 예외를 받지 못한다.
- 이런 경우 uncaughtException 이벤트를 사용해 에러를 처리한다.
- 잡히지 않는 예외가 수신된 후, 실제 운영환경에서는 항상 어플리케이션을 종료하는 것이 좋다.


<details>
<summary>참고</summary>

- Node.js 디자인패턴


</details>