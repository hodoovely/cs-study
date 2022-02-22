
## RESTful API 란 무엇인가?


### 예상 답변

REST 원리를 따르는 API를 RESTful API라고 한다. REST는.. 

----

### 설명 더보기

#### RESTful

REST 원리를 따르는 시스템을 RESTful하다고 한다.

<br/>

#### RESTful 하게 API 를 디자인 한다는 것은 무엇을 의미하는가

***리소스 와 행위 를 명시적이고 직관적으로 분리한다.***
리소스는 URI로 표현되는데 리소스가 가리키는 것은 명사로 표현되어야 한다.
행위는 HTTP Method로 표현하고, GET(조회), POST(생성), PUT(기존 entity 전체 수정), PATCH(기존 entity 일부 수정), DELETE(삭제)을 분명한 목적으로 사용한다.

***Message 는 Header 와 Body 를 명확하게 분리해서 사용한다.***
Entity 에 대한 내용은 body 에 담는다.
애플리케이션 서버가 행동할 판단의 근거가 되는 컨트롤 정보인 API 버전 정보, 응답받고자 하는 MIME 타입 등은 header 에 담는다.
header 와 body 는 http header 와 http body 로 나눌 수도 있고, http body 에 들어가는 json 구조로 분리할 수도 있다.

***API 버전을 관리한다.***
환경은 항상 변하기 때문에 API 의 signature 가 변경될 수도 있음에 유의하자.
특정 API 를 변경할 때는 반드시 하위호환성을 보장해야 한다.

***서버와 클라이언트가 같은 방식을 사용해서 요청하도록 한다.***
브라우저는 form-data 형식의 submit 으로 보내고 서버에서는 json 형태로 보내는 식의 분리보다는 json 으로 보내든, 둘 다 form-data 형식으로 보내든 하나로 통일한다.
다른 말로 표현하자면 URI 가 플랫폼 중립적이어야 한다.

<br/>

#### REST

REST는 월드 와이드 웹(www)과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식이다.

REST(Representational State Transfer)란 자원을 이름(자원의 표현)으로 구분하여 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.

즉 자원(resource)의 표현(representation)에 의한 상태 전달을 말한다.

REST는 ROA(Resource Oriented Architecture)를 따르는 웹 서비스 아키텍쳐이다.

구체적인 의미로는 HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.

<br/>

#### REST의 구성 요소

***자원 (Resource), URI*** :
모든 자원은 고유한 ID를 가지며, 이 ID는 서버에 존재한다.
클라이언트는 각 자원의 상태를 조작하기 위하여 요청을 보낸다.
HTTP에서 이와 같은 자원에 대한 구별 방식의 ID는 flowers/red/1과 같은 HTTP URI이다.

***행위 (Verb), Method*** :
클라이언트는 URI를 이용해 자원을 지정/조작하기 위하여 Method를 사용한다.
HTTP프로토콜에서는 POST, GET, PUT, DELETE를 제공한다.
행위에서 제공하는 Method를 흔히 CRUD Operation이라고 한다.
CRUD Operation, HTTP Method
- Create : POST 자원 생성
- Read : GET 자원 정보 조회
- Update : PUT 자원 정보 업데이트
- Delete : DELETE 자원 삭제

***표현 (Representation)*** :
클라이언트가 서버로 요청을 보냈을 때, 서버가 응답으로 보내주는 자원의 상태를 표현이라고 한다.
REST에서 하나의 자원은 XML, JSON, TEXT등 여러 형태의 표현으로 나타낼 수 있다.

<br/>

#### REST의 특징

***Server-Client(서버-클라이언트 구조)*** :
자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 된다.
REST Server는 API를 제공하고 비즈니스 로직 처리 및 저장을 책임지며, Client는 사용자 인증이나 context(세션, 로그인정보)등을 직접 관리하고 책임진다.
이처럼 각각의 역할이 명확하게 구분되기 때문에, Server와 Client에서 각각 개발해야하는 내용의 의존성이 줄어들게 된다.

***Stateless(무상태성)*** :
이전, 이후에 대한 직접적인 정보가 필요 없이 직관적인 오브젝트에의 접근으로 서비스를 처리한다.
세션정보를 보관할 필요가 없이 들어오는 요청만 단순히 처리하면 되기 때문에, 서비스의 자유도 또한 높아지고 로드밸런싱이라든지 기타 유연한 아키텍쳐의 적용이 가능하다.

***Cacheable(캐시 처리)*** :
웹 표준 HTTP프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 사용할 수 있다.
이에 따라서 HTTP가 가진 캐싱 기능이 적용 가능해지고, HTTP 프로토콜 표준에서 사용하는 Last-Modified태그나 E-Tag를 이용하여 캐싱 구현이 가능해진다.
캐시 사용을 통해 응답시간이 빨라지며 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.

***Hierarchical System(계층 구조)*** :
REST Server는 다중계층으로 구성될 수 있다.
보안, 로드밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고, PROXY나 게이트웨이와 같은 네트워크 기반의 중간매체를 사용할 수도 있다.
Client는 REST API의 Server만을 호출한다.

***Uniform Interface(인터페이스 일관성)*** :
URI로 지정한 리소스 조작을 통일되고 한정적인 인터페이스로 수행한다.

***Code on demand(계층 구조)(optional)*** :
(배포 후) 서버에서 클라이언트로 코드를 보내서, 클라이언트에서 코드를 실행하여 기능을 확장할 수 있는 것을 의미한다.

<br/>

#### REST의 장점
- HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API를 위한 별도의 인프라를 구축할 필요 없다.
- HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 사용할 수 있다.
- HTTP표준 프로토콜을 따르는 모든 플랫폼에서 사용 가능하다.
- Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다.
- REST API가 의도하는 바를 명확히 나타내 의도하는 바를 쉽게 파악할 수 있다.
- Server와 Client의 역할을 명확하게 분리한다.
- 원하는 타입으로 데이터를 주고받을 수 있다.
- Open API를 제공하기가 쉽다.
- 멀티플랫폼 지원 및 연동이 용이하다.

<br/>

#### REST의 단점

- 사용할 수 있는 Method가 네 가지밖에 없다는 한계가 있다.
- 명확한 표준이 없다.
- 분산환경에는 부적합하다.
- HTTP통신 모델에 대해서만 지원하며, 구형 브라우저가 지원하지 못하는 부분들(PUT, DELETE, pushState)이 존재한다.

﻿
