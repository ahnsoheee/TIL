## DNS (Domain Name System)

![image](https://user-images.githubusercontent.com/61968474/135806280-ef677953-234f-4db2-b973-cefe5c312bdf.png)

### 도메인 네임
- 넓은 의미 : 네트워크 상에서 컴퓨터를 식별하는 호스트명
- 좁은 의미 : 도메인 레지스트리에 등록된 이름

- 도메인은 “.”또는 루트(root)라 불리는 도메인 이하에 그림과 같이 역트리(Inverted tree)구조로 구성되어 있다.
- 루트 도메인 바로 아래의 단계를 1단계 도메인 또는 최상위 도메인(TLD, Top Level Domain)이라고 부른다.
- 그 다음 단계를 2단계 도메인(SLD, Second Level Domain)이라고 부른다
- 도메인의 계층 구조는 오른쪽부터 왼쪽으로 내려간다.


### DNS

- 인터넷 트래픽을 한 곳에서 담당할 수 없기 때문에 분산되어 설계되었다.
- 분산하기 위해 많은 서버를 이용하고 계층 형태로 구성하여 전 세계에 분산시켰다.
- **루트 DNS 서버** / **최상위 레벨 도메인 네임 DNS 서버** (TLD: top-level domain) / **책임 DNS 서버**가 트리 형태로 구성된다.

#### 1. 루트 DNS 서버

- 도메인 Name space의 최고점에 있는 정보를 보유한 네임서버로 인터넷의 핵심을 담당하는 중요한 서버

#### 2. 최상위 레벨 도메인 서버

- com, org, net, edu 와 같은 상위 레벨 도메인과 kr, jk, fr 등 모든 국가의 상위 레벨 도메인을 포함한다.

#### 3. 책임 DNS 서버

- 인터넷에서 접근하기 쉬운 페이지를 가진 기관은 호스트 네임을 IP주소로 연결 시키는 역할을 한다.

- ex) www.google.com

- [www.google.com](http://www.google.com) : 최상위 도메인 com에 속한다.

- google : 도메인의 서브 도메인

- www : google.com의 서브 도메인

    ⇒ DNS 계층 구조를 거쳐 사용자에게 서비스를 제공한다.