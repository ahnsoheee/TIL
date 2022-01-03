## SOLID 원칙

- 객체지향 설계에서 지켜야 하는 5개의 원칙

### 1. Single Responsiblity Principle (단일 책임 원칙,  SPR) 
- 클래스, 함수 등은 단 하나의 책임을 가져야 한다.
- 응집도는 높게, 결합도는 낮게 설계하는 것이 좋다.
- 가독성이 좋아지고 유지보수가 쉬워지며, 재사용성이 높아진다.

### 2.  Open-Closed Primciple (개방-폐쇄 원칙, OCP) 
- 기존의 코드를 변경하지 않고 (Closed) 기능을 수정하거나 추가할 수 있도록 (Open) 설계해야 한다.

### 3.  Liskov Substitution Principle (리스코프 치환 원칙, LSP) 
- 부모 클래스와 자식 클래스 사이의 일관성이 있어야 한다.
- 부모 클래스의 인스턴스 대신 자식 클래스의 인스턴스를 사용해도 문제가 없어야 한다.

### 4. Dependency Inversion Principle (의존 역전 원칙, DIP) 
- 의존 관계를 맺을 때, 변화하기 쉬운 것(구체적인 것) 보다 변화하기 어려운 것(추상적인 것)에 의존해야 한다.
- DIP를 만족한다는 것은 구체적인 클래스보다 인터페이스나 추상 클래스와 관계를 맺는다는 것을 의미한다.

### 5. Interface Segregation Principle (인터페이스 분리 원칙. ISP) 
- 한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다.
- 하나의 일반적인 인터페이스보다 여러 개의 구체적인 인터페이스가 낫다
- 즉, 자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지 말아야 한다.

#### 참고 
- [링크](https://dev-momo.tistory.com/entry/SOLID-%EC%9B%90%EC%B9%99)