# REST API
> REST(REpresentational State Transfer): 웹(HTTP) 의 장점을 활용한 아키텍쳐<br/>
> URI를 통해 자원을 명시하고 Method를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것

### REST의 요소
* Method
  * HTTP protocol Method
* Resource
  * http://myweb/users와 같은 URI
  * 모든 것을 Resource로 표현하고 세부 Resource에는 id를 붙임
* Message
  * 메시지 포맷이 존재(JSON, XML)

### REST가 필요한 이유
* 다양한 클라이언트의 등장으로 웹, IOS, 안드로이드 모든 클라이언트에 맞춰 각각의 통신을 구축하기 보다 애플리케이션의 분리 및 통합이 용이한 REST API가 대두되었다.

### REST 특징
* Server-Client 구조
  * REST Server: API제공, 비즈니스 로직 처리 및 저장
  * Client: 사용자 인증이나 context 등을 직접 관리하고 책임진다.
  * 의존성이 줄어든다
* Stateless (무상태성)
  * HTTP 프로토콜의 특징인 Stateless를 그대로 갖는다.
  * Client의 context를 Server에 저장하지 않는다.
* Cacheable (캐시 처리 가능)
  * HTTP 프로토콜을 그대로 사용하므로 캐싱 기능을 적용할 수 있다.
  * 대량의 요청을 효율적으로 처리할 수 있다.
  * 응답시간이 빨라지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.
* Uniform Interface (인터페이스 일관성)
  * URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행한다.
  * HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능
    * 특정 언어나 기술에 종속되지 않는다.

### REST API
* REST 기반의 서비스 API 구현체
* 시스템이 분산되어 확장성과 재사용성이 높아지고 유지보수 및 운용이 편리하다.
* REST는 HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램언어로 클라이언트, 서버를 구현할 수 있다.

### REST-ful
* REST API를 제공하는 웹 서비스를 RESTful하다고 할 수 있다.
* REST 원리를 따르는 시스템은 RESTful 이라고 지칭된다.