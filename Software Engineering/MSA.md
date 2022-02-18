## MSA (Micro Service Architecture) 

### 마이크로서비스 아키텍처의 특징
- 애플리케이션 로직을 각자 책임이 명확한 작은 컴포넌트들로 분해하고 이들을 조합해서 솔루션을 제공한다.
- 각 컴포넌트는 작은 책임 영역을 담당하고 완전히 상호 독립적으로 배포된다. 마이크로서비스는 비즈니스 영역의 한 부분에서만 책임을 담당한다. 그리고 여러 애플리케이션에서 재사용할 수 있어야 한다.
- 마이크로서비스는 몇 가지 기본 원칙(표준 x)에 기반을 두며, 서비스 소비자와 서비스 제공자 사이의 데이터 교환을 위해 HTTP와 JSON 같은 경량 통신 프로토콜을 사용한다.
- 애플리케이션은 항상 기술 중립적 프로토콜(JSON)을 사용해 통신하므로 서비스 구현 기술과는 무관하다. 마이크로 서비스 기반의 애플리케이션을 다양한 언어와 기술로 구축할 수 있다는 의미이다.
- 작고 독립적이며 분산된 마이크로서비스를 사용해 조직은 명확이 정의된 책임 영역을 담당하는 소규모 팀을 보유할 수 있다. 하나의 목표를 향하지만, 자기가 개발하는 서비스만 책임진다.

=> 분산되고 느슨하게 결합된 소프트웨어 서비스 구조, 상호 독립적인 최소 구성 요소로 분리
**명확한 모듈 경계, 독립적 배포, 기술 다양성**
_이상적인 설계 방법이지만, 구축이 어렵다!!_

### DevOps - 생명 주기

#### 1. 서비스 어셈블리
- 필요한 의존성을 모두 담아 단일 산출물로 패키징하고 배포하는 과정
- 어셈블리 단계에서 소스 코드를 컴파일하고 런타임 엔진과 함께 패키징한다.

#### 부트스트래핑
- 마이크로 서비스가 처음 가동할 때 시작하며, 애플리케이션 구성 정보를 로딩한다.
- 애플리케이션 구성 정보는 시작하는 서비스의 환경 변수로 전달하고, 구성 관리를 위한 중앙 저장소에서 읽어온다.

#### 디스커버리
- 마이크로서비스 인스턴스는 제3자 에이전트에 등록하는 과정
- 클라우드 기반 환경의 서버는 일시적이기 대문에 위치 투명성을 가져야 한다.
- 서비스를 일시적이고 폐기 가능한 객체로 취급하기 때문에 마이크로서비스 아키텍처는 많은 서비스 인스턴스를 실행하며 확장성과 가용성을 얻을 수 있다.
- 모든 서비스에 고유하고 비영구적인 IP 주소가 할당된다.
- 마이크로서비스 인스턴스를 서비스 디스커버리 에이전트에 등롤할 때 인스턴스의 물리적인 IP주소 / 도메인 주소, 애플리케이션이 서비스 검색에 사용할 논리적인 서비스 이름을 에이전트에 전달한다.

#### 모니터링
- 서비스 디스커버리 에이전트는 등록된 각 서비스 상태를 모니터링한다.
- 클라이언트가 고장난 서비스를 호출하지 않도록 자신의 라우팅 테이블에서 문제가 된 서비스 인스턴스를 제거한다.
대부분의 서비스 인스턴스는 에이전트가 호출할 상태 확인용 URL을 노출한다. HTTP 에러가 반환되거나 제 시간에 응답을 받지 않는다면 에이전트는 그 인스턴스를 강제 종료하거나 트래픽을 받지 않도록 우회시킨다.
- REST 기반 마이크로서비스 환경에서 상태 확인 인터페이스를 만드는 가장 단순한 방법은 JSON 페이로드와 HTTP 상태 코드를 반환하는 HTTP 엔드포인트를 노출하는 것이다.

<details>
<summary>참고</summary>

- 스프링 마이크로서비스 코딩 공작소


</details>