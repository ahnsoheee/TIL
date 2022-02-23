## module.exports vs exports

- exports (참조)-> module.exports (참조)-> {}
- exports에 멤버를 추가하면 module.exports에도 같은 멤버가 추가된다.
- exports 객체에는 값을 할당할 수 없고 프로퍼티, 메소드로 추가한다.
```js
exports.add = () => {}
```
- exports에 다른 값을 대입하면 객체의 참조 관계가 끊겨 더 이상 모듈로 기능하지 않는다.
- **module.exports와 exports는 call by reference로 동일한 객체를 바라보고 있고, 리턴되는 값은 항상 module.exports** (모듈은 캐시되기 때문에 동일한 객체를 공유한다.)