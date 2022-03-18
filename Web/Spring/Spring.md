## Spring

- 자바 플랫폼을 위한 오픈 소스 애플리케이션 프레임워크

### 특징
![image](https://user-images.githubusercontent.com/61968474/158604501-ca74c4be-f273-4631-901f-9f61be4c40c1.png)

#### 1. IoC 컨테이너를 갖는다
- IoC (Inversion of Control): 제어의 역전
- 주도권이 스프링에게 있다. 
    - 객체 생성, 생명 주기 관리 등 객체에 대한 제어권이 바뀐다.
- IoC 컨테이너는 객체의 생성을 책임지고, 의존성을 관리한다.
- POJO의 생성, 초기화, 서비스, 소멸에 대한 권한을 가진다.

#### 2. DI를 지원한다.
- DI(Dependency Injection): 의존성 주입
- 스프링이 관리하는 객체를 (모든 클래스의 메소드에서) 사용할 수 있다.
    - 싱글톤: 객체는 메모리에 한 번만 로드되고 전역에서 사용할 수 있다.
- 각 클래스 간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해준다.

#### 3. 많은 필터를 가진다.
- 필터를 생성할 수도 있다.
- 권한 체크 등등

#### 4. 많은 어노테이션을 가진다.
- 어노테이션: 컴파일러가 읽는 주석
- 컴파일 체킹
    - ex) Override: 상속 관계에서 부모 클래스에 없는 자식클래스의 메소드에 달면 컴파일 에러
- 어노테이션을 통해 객체를 생성한다.
    - Autowired: 로딩된 객체를 해당 변수에 연결한다. 타입을 통해 같은 타입이 있으면 해당 변수를 할당(DI)하고, 없으면 null
    - Component: 스프링이 해당 클래스를 읽고 메모리에 로딩한다. (IoC)
- 리플렉션: 해당 클래스가 어떤 필드, 메소드, 어노테이션을 가진지 분석하는 기법 (런타임 시)

#### 5. 메시지 컨버터를 가진다.
- JSON Object로 변경: 자바 Object -> JSON / JSON -> 자바 Object
- 컨버터: Jackson
- request 시 JSON으로 변경, response 받을때 자바 Object로 변경

#### 6. BufferedReader와 BufferedWriter를 쉽게 사용할 수 있다. (ByteStream으로 데이터를 주고 받음)
- InputStreamReader: InputStream(바이트) -> 문자(Character)
- BufferedReader: 가변 길이로 받을 수 있다.
- BufferedWriter: 가변 길이 문자열로 데이터를 쓸 수 있다.


### 프레임워크 모듈

#### 스프링 AOP
- 스프링 빈에만 적용이 가능하다.
- 모든 AOP 기능을 제공하는 것이 아니라 스프링 IoC와 연동해 중복 코드, 객체 간 관계 복잡도 증가 등에 대한 해결책을 지원하는 것이 목적이다.
- 프록시 패턴 기반의 AOP 구현체이며 접근 제어 및 부가 기능을 추가하기 위해 프록시 객체를 사용한다.
- 클래스에 @Component로 빈 등록을 하고 @Aspect 어노테이션으로 명시한다.

<details>
<summary>AOP란</summary>

### AOP (Aspect Oriented Programming)

- 관점 지향 프로그래밍
- 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누고 그 관점을 기준으로 모듈화하는 것 (모듈화: 공통된 로직이나 기능을 하나의 단위로 묶는 것)
-> Aspect로 모듈화하고 핵심적인 비즈니스 로직에서 분리해 재사용하는 것이 AOP의 취지

</details>

#### Messaging
- 미시지 기반 어플리케이션을 작성할 수 있는 Message, MessageChannel, MessageHandler 등을 제공한다.
- 해당 모듈에는 메소드에 메시지를 매핑하기 위한 어노테이션이 포함되어 있고, Spring MVC 어노테이션과 유사하다.

#### Data Access / Integration
- 데이터 액세스/통합 계층은 JDBC, ORM 및 트랜잭션 모듈로 구성되어 있다.
- spring-jdbc: 자바 JDBC 프로그래밍을 쉽게 할 수 있도록 기능을 제공한다.
- spring-tx: 선언적 트랜잭션 관리를 할 수 있는 기능을 제공한다.
- spring-orm: JPA, Hibernate를 포함한 ORM API를 위한 통합 레이어를 제공한다.
- spring-oxm: XMLBeans, JiBX, XStream과 같은 Object/XML 매핑을 지원한다.
- spring-jms: 메시지 생성 및 사용을 위한 기능을 제공하고 Spring Framework 4.1부터 spring-messaging모듈과의 통합을 제공한다.

#### Web
- 웹 계층은 spring-web, spring-webmvc, spring-websocket, spring-webmvc-portlet 모듈로 구성된다.
- spring-web: 멀티 파트 파일 업로드, 서블릿 리스너 등 웹 지향 통합 기능을 제공한다. HTTP 클라이언트와 Spring의 원격 지원을 위한 웹 관련 부분을 제공한다.
- spring-websocket: 웹 소켓을 지원한다.
- spring-webmvc-portlet: 포틀릿 환경에서 사용할 MVC 구현을 제공한다.

### Spring IoC/DI 컨테이너
- BeanFactory: 빈을 생성하고 분배하는 등 IoC/DI에 대한 기본 기능을 가진다.
- ApplicationContext: BeanFactory의 모든 기능을 포함하며, 일반적으로 BeanFactory보다 추천된다.
    - 트랜잭션처리, AOP 등에 대한 처리를 할 수 있다.
    - BeanPostProcessor, BeanFactoryPostProcessor 등을 자동으로 등록하고, 어플리케이션 이벤트 등을 처리할 수 있다.
- BeanPostProcessor: 컨테이너의 기본 로직을 오버라이딩해 인스턴스화와 의존성 처리 로직 등을 개발자가 원하는 대로 구현할 수 있다.
- BeanFactoryPostProcessor: 설정된 메타 데이터를 커스터마이징할 수 있다.
- 스프링을 DI 컨테이너라고도 한다.

### Bean
- new 연산자로 생성한 객체는 빈이라고 하지 않는다.
- Spring은 빈을 생성할 때 기본적으로 싱글톤 객체로 생성한다.
- 동시에 서로 다른 빈을 사용해야하는 경우 Spring에서 빈을 생성할 때 스코프를 줌으로써 기본으로 설정된 싱글톤 외에도 객체를 생성할 수 있다.
- Singleton Scope Bean의 동시성 문제를 해결하기 위해 synchronized() 블록으로 임계 구역을 감싸 해결할 수 있다.


#### 특징
- 기본 생성자를 가진다.
- 필드는 private하게 선언한다.
- getter, setter 메소드를 가진다.
- getName(), setName() 메소드를 name 프로퍼티(property)라고 한다.

#### src/main/resources/applicationContext.xml
```java
...
<bean id="userBean" class="~~.UserBean"></bean>
```

#### ApplicationContextEx1.java
```java
...
import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

public class ApplicationContextEx1 {
    public static void main(String[] args) {
        ApplicationContext ac = new ClassPathXmlApplicationContext("classpath:applicationContext.xml");
        System.out.println("초기화 완료");

        UserBean userBean = (UserBean)ac.getBean("userBean");
        userBean.setName("kim");
        System.out.println(userBean.getName());

        UserBean userBean2 = (UserBean)ac.getBean("userBean");
        if (userBean == userBean2) {
            System.out.println("같은 인스턴스이다.");
        }
    }
}

```
<details>
<summary>참고</summary>

- [AOP](https://engkimbs.tistory.com/746)

</details>
