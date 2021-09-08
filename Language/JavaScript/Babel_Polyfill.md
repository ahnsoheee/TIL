## 1. Babel

- ES6+ 문법을 ES5 이하의 문법으로 변환해주는 트랜스 컴파일러
- Arrow function을 지원하지 않는 브라우저에서는 Syntax오류가 발생하기 때문에 자바스크립트가 읽을 수 있는 스크립트로 재작성되어 새로 컴파일 된다.
- babel은 문법 변환 역할만 한다.

**⇒ 구 브라우저에서도 최신 자바스크립트가 작동하도록 변환해주는 컴파일러(트랜스파일러)**

## 2. Polyfill

- 자바스크립트의 문법이지만 브라우저에서 지원되지 않는 객체나 메소드 등을 사용할 수 있도록 변환해주어 호환성을 채워넣는다는 의미
- 프로그램을 실행할 때(런타임) 현재 브라우저에서 지원하지 않는 함수를 검사(브라우저가 실행되는 시점에 동작)해서 변환한다.
- 각 객체의 prototype에 붙여준다.
- 새로 추가된 전역 객체들(Promise, Map, Set 등; ES6)나 메소드(String.padStart()) 등을 사용가능한 객체로 바꿔준다.

## 3. Babel vs Polyfill

- Babel : 자바스크립트의 Syntax가 아닌 것들을 자바스크립트에서 사용할 수 있게 문법만 바꿔준다.
- Polyfill : 자바스크립트의 Syntax이지만 정의되지 않은 객체나 메소드들을 사용할 수 있도록 해준다.
⇒  구 브라우저에서 최신 자바스크립트를 사용하기 위해서 babel을 사용하지만, 일부 기능들은 polyfill로 추가해주어야한다.

## 4. babel-polyfill

- babel 만으로는 ES6+의 내장 메소드는 대체 불가하기 때문에 babel-polyfill을 추가해야 한다.
- ES6+에서 새롭게 추가된 객체를 브라우저에서 동작할 수 있도록 변환해준다.

  -> babel 7.4.0 이후 버전부터 babel-polyfill을 직접 사용하기 때문에 따로 설치할 필요가 없다.

```jsx
const test = (a, b) => a * b

-> var test = function test(a, b) { return a * b } 로 변환
```

<u>**기존의 Polyfill**</u>

- babel-polyfill을 추가하거나 transform-runtime(regenerator + core-js)을 해야했다.

- @babel/polyfill : 제너레이터 폴리필인 regenerator-runtime + core-js 폴리필

    -> 전역 공간에 폴리필을 채워넣는 방식이기 때문에 폴리필 충돌 가능성이 있다는 단점이 있다.

    -> babel 7.4.0 이후 deprecated  => core-js + regenerator-runtime 방식 제안

- transform-runtime : 플러그인으로 추가하면 되었지만 인스턴스 메소드는 동작하지 않았다. ( [1, 2, 3].includes x )

## 5. core-js@3

- @babel/polyfill의 전역공간 오염 문제와 바벨 런타임 플러그인의 인스턴스 메소드 문제를 해결한 런타임 폴리필

## 6. plugin

- 어떤 코드를 어떻게 판단할지에 대한 규칙 (@babel/plugin-transform-.... : 변환 플러그인 / @babel/plugin-syntax-.... : 문법 플러그인)
- babel이 특정 유형의 syntax만 분석하도록 허용한다
- parsing (구문 분석) → transformation (변환) → printing (출력)
- 실제로 동작하는 것은 plugin
- plugin과 preset을 추가하지 않으면 babel은 아무것도 하지 않는다.
- babelrc : babel plugin들을 모아놓고 사용할 설정파일

## 7. preset

- plugin을 모아둔 것 (번들)
- 자주 쓰이는 특정 플러그인들의 조합
- npm 설치와 babel 설정을 한번만 하면 plugin들이 자동적으로 설치된다.
- ex) naver, airbnb, google
