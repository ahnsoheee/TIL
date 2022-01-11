## Generator
- 세미 코루틴(semi-coroutines)
- 다른 진입점이 있을 수 있는 서브 루틴들을 일반화한 것
- 함수와 비슷하지만 일시적으로 실행의 흐름을 중지시켰다가, 다시 시작시킬 수 있다.
- Iterator(반복자)를 구현하는데 유용하다.
- function 키워드 다음에 * 연산자를 추가하여 선언한다.

```js
function* makeGenerator() {
    yield 'Hello World'; // yield: 값을 반환하거나 주입 받음
    console.log('Re-entered';)
}

const gen = makeGenerator();
```
- makeGenerator() 함수는 호출될 때 새로운 제너레이터 객체를 반환하는 팩토리(factory)
- next() : 제너레이터의 실행을 시작/재시작하는데 사용된다.
- 다음과 같은 형식의 객체를 반환한다.
```js
{ 
    value: <yield시 반환값>
    done: <제너레이터가 끝났는지 여부>
}
```

### example
```js
function* fruitGenerator() {
    yield 'apple';
    yield 'orange';
    return 'watermelon';
}

const newFruitGenerator = fruitGenerator();
console.log(newFruitGenerator.next())
console.log(newFruitGenerator.next())
console.log(newFruitGenerator.next())

// { value: 'apple', done: false }
// { value: 'orange', done: false }
// { value: 'watermelon', done: true }

```
- newFruitGenerator.next()가 처음으로 호출되었을 때, 제너레이터는 첫 번째 yield 명령에 도달할 때까지 실행을 계속한다. 이 명령은 제너레이터를 일시 중지시키고 값 apple을 호출자에게 반환한다.
- newFruitGenerator.next()가 두 번째 호출하면 제너레이터는 두번 째 yield 명령에서 실행을 시작해 다시 실행을 일시 중지하고 orange 값을 반환한다.
- newFruitGenerator.next()의 마지막 호출은 제너레이터의 마지막 명령으로 제너레이터를 끝내는 return 문에서 재시작해 value를 watermelon으로 설정하고 done을 true로 설정하여 반환한다.

### 제너레이터로 반복자(Iterator) 구현
```js
function* iteratorGenerator(arr) {
    for (let i=0; i<arr.length; i++) {
        yield arr[i];
    }
}

const iterator = iteratorGenerator(['apple', 'orange', 'watermelon']);
let currentItem = iterator.next();
while(!currentItem.done) {
    console.log(currentItem.value);
    currentItem = iterator.next();
}

// apple
// orange
// watermelon
```

### 값을 제너레이터로 전달하기
```js
function* twoWayGenerator() {
    const what = yield null;
    console.log('Hello ' + what);
}

const twoWay = twoWayGenerator();
twoWay.next();
twoWay.next('world');

// Hello world
```
- next()가 처음 호출되면 제너레이터는 첫 번재 yield 문에 도달한 다음, 일시 중지 상태가 된다.
- next('world')가 호출되면 제너레이터는 yield 명령에 있는 일시 중지 지점에서 다시 시작되지만, 이번에는 제너레이터로 전달되는 값을 갖고 있기 때문에 what 변수에 값이 설정된다.
- 제너레이터는 console.log() 명령을 실행하고 종료한다.
