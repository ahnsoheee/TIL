## Babel
- 트랜스 컴파일러

- 자바스크립트 컴파일러 → 자바스크립트로 결과물을 만들어주는 컴파일러
- ES6/7 코드를 ES5 코드로 변환해주는 변환기 → 호환되는 버전으로 변환
- Arrow function을 지원하지 않는 브라우저에서는 Syntax오류가 발생하기 때문에 자바스크립트가 읽을 수 있는 스크립트로 재작성되어 새로 컴파일 된다.
- babel은 문법 변환 역할만 한다.

**⇒ 구 브라우저에서도 최신 자바스크립트가 작동하도록 변환해주는 컴파일러(트랜스파일러)**

## Polyfill

- 특정 기능이 지원되지 않는 브라우저를 위해 사용할 수 있는 코드로 바꿔준다.
- 프로그램이 시작될 때 현재 브라우저에서 지원하지 않는 함수를 검사한다.

    → 브라우저가 실행되는 시점에 동작

- 각 객체의 prototype에 붙여준다.
- 브라우저에서 지원하지 않는 기능들에 대한 호환성 작업을 채워 넣는다는 의미
- 새로 추가된 전역 객체들(Promise, Map, Set 등; ES6)나 메소드(String.padStart) 등을 사용가능한 객체로 바꿔준다.

## Babel vs Polyfill

- Babel : 자바스크립트의 Syntax가 아닌 것들을 자바스크립트에서 사용할 수 있게 문법만 바꿔준다.
- Polyfill : 자바스크립트의 Syntax이지만 정의되지 않은 객체나 메소드들을 사용할 수 있도록 해준다.
⇒  구 브라우저에서 최신 자바스크립트를 사용하기 위해서 babel을 사용하지만, 일부 기능들은 polyfill로 추가해주어야한다.

### Babel-polyfill

- 자바스크립트의 최신 문법으로 코딩하면, babel 패키지가 웹브라우저간의 호환성을 책임진다.
- 구문(Syntax) 변환
- 소스코드 변환

```jsx
const test = (a, b) => a * b

-> var test = function test(a, b) { return a * b } 로 변환
```

- babel은 **컴파일** 타임에 실행되고 babel-polyfill은 **런타임**에 실행된다.

## plugin

- 어떤 코드를 어떻게 판단할지에 대한 규칙 (@babel/plugin-transform-.... : 변환 플러그인 / @babel/plugin-syntax-.... : 문법 플러그인)
- babel이 특정 유형의 syntax만 분석하도록 허용한다
- parsing (구문 분석) → transformation (변환) → printing (출력)
- 실제로 동작하는 것은 plugin
- plugin과 preset을 추가하지 않으면 babel은 아무것도 하지 않는다.
- babelrc : babel plugin들을 모아놓고 사용할 설정파일

## preset

- plugin을 모아둔 것 (번들)
- 자주 쓰이는 특정 플러그인들의 조합
- npm 설치와 babel 설정을 한번만 하면 plugin들이 자동적으로 설치된다.
- ex) naver, airbnb, google
