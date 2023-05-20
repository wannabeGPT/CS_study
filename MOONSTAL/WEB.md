# WEB

## ****브라우저 동작 방법****

### 방법

- 주소창에 url을 입력
- 서버에 요청이 전송
- 해당 페이지에 자원들(text, image 등등)이 보내짐
- 렌더링 엔진 html 파싱, html 파서가 DOM 트리를 구축
- css 파싱: css 파서가 스타일 구조체로 생성
- 2가지를 연결시켜 렌더 트리생성(시각적 요소를 포함한 형태)
- 화면에 배치
- 기다리는 동시에 일부분 먼저 진행
- 렌더링: 요청 받은 내용을 브라우저 화면에 표시

### **DOM(Document Object Model(문서 객체 모델)**

- `<html>, <body>`와 같은 태그→Javascript가 활용할 수 있는 객체로 만들면 `문서 객체`
- DOM은 웹 브라우저가 html 페이지를 인식하는 방식

### ****[www.naver.com](http://www.naver.xn--com-568n/)에 접속할 때 생기는 과정**

1. 사용자가 브라우저에 URL([www.naver.com](http://www.naver.com/))을 입력
2. DNS 서버에 도메인 네임으로 서버의 진짜 주소를 찾음
3. IP 주소로 웹 서버에 TCP 3 handshake로 연결 수립
4. 클라이언트는 웹 서버로 HTTP 요청 메시지를 보냄
5. 웹 서버는 HTTP 응답 메시지를 보냄
6. 도착한 HTTP 응답 메세지는 웹 페이지 데이터로 변환되고, 웹 브라우저에 의해 출력

[https://gyoogle.dev/blog/web-knowledge/브라우저 동작 방법.html](https://gyoogle.dev/blog/web-knowledge/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%20%EB%8F%99%EC%9E%91%20%EB%B0%A9%EB%B2%95.html)

[https://dev-coco.tistory.com/161#head3](https://dev-coco.tistory.com/161#head3)

## 쿠키 & 세션

|  | 쿠키(Cookie) | 세션(Session) |
| --- | --- | --- |
| 설명 | 사용자의 컴퓨터에 저장하는 작은 기록 정보 파일 | 방문자가 웹 서버에 접속해 있는 상태
*Session ID로 클라이언트를 구분해 각 요구에 맞는 서비스를 제공 |
| 저장 위치 | 클라이언트(=접속자 PC) | 웹 서버 |
| 저장 형식 | text | Object |
| 만료 시점 | 쿠키 저장시 설정(브라우저가 종료되도, 만료시점이 지나지 않으면 삭제되지 않음) | 브라우저 종료시 삭제(기간 지정 가능) |
| 사용하는 자원(리소스) | 클라이언트 리소스 | 웹 서버 리소스 |
| 용량 제한 | 총 300개하나의 도메인 당 20개하나의 쿠키 당 4KB(=4096byte) | 서버가 허용하는 한 용량제한 없음 |
| 속도 | 세션보다 빠름 | 쿠키보다 느림 |
| 보안 | 세션보다 안좋음 | 쿠키보다 좋음 |
- **캐시**는 웹 페이지를 빠르게 렌더링
- 쿠키/세션은 사용자의 인증

[https://dev-coco.tistory.com/61](https://dev-coco.tistory.com/61)

## HTTP Request Methods

| 처리 방식 | GET 방식 | POST 방식 |
| --- | --- | --- |
| URL에 데이터 노출 여부 | O | X |
| URL 예시 | http://localhost:8080/boardList?name=제목&contents=내용 | http://localhost:8080/addBoard |
| 데이터의 위치 | Header(헤더) | Body(바디) |
| 캐싱 가능 여부 | O | X |
| 멱등성 여부 | O | X |
- ****GET****
    - 데이터 받기
    - URL(URI) 형식 요청
    - url→데이터의 크기 제한
    - 데이터가 그대로 url 에 노출→보안X
- ****POST****
    - 내용 및 파일 전송
    - Request 데이터를 HTTP Body에 담아 전송
    - 데이터 크기가 GET 방식보다 크고 보안면에서 낫다
- ****PUT****
    - 데이터를 갱신
- ****DELETE****
    - 데이터 삭제
- ****PATCH****
    - 데이터의 일부분만 갱신
- ****HEAD****
    - 메세지 헤더 정보
- ****OPTIONS****
    - 웹 서버 측에서 지원하고 있는 메소드 확인

[https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Network#http의-get과-post-비교](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Network#http%EC%9D%98-get%EA%B3%BC-post-%EB%B9%84%EA%B5%90)

[https://dev-coco.tistory.com/60](https://dev-coco.tistory.com/60)

## HTTP status code

- 상태 코드: 클라이언트가 보낸 요청의 처리 상태 응답
- 1xx: 요청 수신 처리중
- 2xx: 요청 성공
    - 200 ok: 요청 성공
    - 201 created: 새로운 리소스 생성
    - 202 accepted: 요청접수o 처리x 배치
    - 204 no content: 보낼 데이터 없음
- 3xx: 웹 브라우저 추가 행동 필요
    - 리다이렉션: location위치로 이동, 영구, 일시, 특수
    - 301(get, 본문제거), 308(요청메서드, 본문유지): uri가 영구적으로 이동
    - 302(get, 본문제거), 307(요청메서드, 본문유지), 303(get): 일시적 리다이렉션
    - prg: post/redirect/get, 새로고침으로 인한 중복주문 방지
    - 304: 캐시 목적, 리소스 수정x, 재사용
- 4xx: 클라이언트 오류
    - 400 Bad Request: 요청 파라미터, api스펙 잘못
    - 401 Unauthorized: 리소스에 대한 인증 필요 (인증-로그인)
    - 403 Forbidden: 인증 o, 접근 권한x (인가-권한)
    - 404 Found: 리소스 서버에 없음
- 5xx: 서버오류
    - 500 Internal Server Error: 서버 내부 문제
    - 502 Bad Gateway: 게이트웨이 오류
    - 503: 서버 일시적 과부화/예정 작업 -> 서비스 이용불가

[https://moonstal.tistory.com/129](https://moonstal.tistory.com/129)

## REST API

- REST 는 `Resource Oriented Architecture`
- 어떤 자원에 대해 CRUD 수행 시 URI는 정보의 자원만 표현해야 하며, 자원의 상태와 행위는 HTTP Method에 명시

### ****REST의 요소****

- **Method 행위**
- ****Resource 자원: URI 모든 것을 Resource (명사)로 표현****
- ****Message: JSON, XML****

### ****REST의 특징****

- **Server-Client (서버-클라이언트 구조)**
- **Stateless (무상태)**
- **Cacheable (캐시 처리 기능)**
- **Layered System (계층 구조-보안, 로드 밸런싱, 암호,Proxy, Gateway)**
- **Uniform Interface (인터페이스 일관성): 특정 언어나 기술에 종속되지 않음**
- **Self-Descriptiveness (자체 표현)**

[https://dev-coco.tistory.com/97](https://dev-coco.tistory.com/97)

## Web Server와 WAS

### **Web Server**

- **정적 컨텐츠**를 제공하는 서버
- 단순 HTML 문서, CSS, 이미지, 파일 응답
- Apache, NginX

### **WAS(Web Application Server)**

- DB 조회 혹은 다양한 로직 처리를 요구하는 **동적 컨텐츠**를 제공하는 서버
- JSP, Servlet 구동환경을 제공해주기 때문에 서블릿 컨테이너 혹은 웹 컨테이너로 불린다.
- 프로그램 실행 환경과 DB 접속 기능을 제공, 여러 개의 트랜잭션을 관리, 비즈니스 로직 수행
- Tomcat, JBoss

### **웹 서버와 WAS 분리이유**

- 서버 부하 방지
- 보안 강화-SSL에 대한 암호화, 복호화 처리(웹 서버)
- 여러 대의 WAS 연결 가능-로드 밸런싱
- 여러 웹 어플리케이션 서비스 가능

[https://code-lab1.tistory.com/199](https://code-lab1.tistory.com/199)

## OAuth

Open Authorization

다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 개방형 표준 방법

### ****용어****

- **사용자** : 계정을 가지고 있는 개인
- **소비자** : OAuth를 사용해 서비스 제공자에게 접근하는 웹사이트 or 애플리케이션
- **서비스 제공자** : OAuth를 통해 접근을 지원하는 웹 애플리케이션
- **소비자 비밀번호** : 서비스 제공자에서 소비자가 자신임을 인증하기 위한 키
- **요청 토큰** : 소비자가 사용자에게 접근권한을 인증받기 위해 필요한 정보가 담겨있음
- **접근 토큰** : 인증 후에 사용자가 서비스 제공자가 아닌 소비자를 통해 보호 자원에 접근하기 위한 키 값

### 인증 과정

1. 소비자가 서비스 제공자에게 요청토큰을 요청한다.
2. 서비스 제공자가 소비자에게 요청토큰을 발급해준다.
3. 소비자가 사용자를 서비스제공자로 이동시킨다. 여기서 사용자 인증이 수행된다.
4. 서비스 제공자가 사용자를 소비자로 이동시킨다.
5. 소비자가 접근토큰을 요청한다.
6. 서비스제공자가 접근토큰을 발급한다.
7. 발급된 접근토큰을 이용해서 소비자에서 사용자 정보에 접근한다.

[https://gyoogle.dev/blog/web-knowledge/OAuth.html](https://gyoogle.dev/blog/web-knowledge/OAuth.html)

## JWT****(Json Web Token)****

- Stateless 상태를 유지하며, 서버에서 사용자를 식별할 수 있는 수단을 제공
- 서버에서 사용자 인증되면 JWT 반환
- 클라이언트는 JWT를 로컬 영역에 저장하고, 이후 서버에 요청을 보낼 때 JWT를 HTTP 헤더에 포함
- 구조
    - Header: JWT를 검증하는데 필요한 정보(토큰 타입, 사용된 알고리즘)
    - Payload: JWT를 통해 전달하고자 하는 데이터(Claim-Set:Key-Value 데이터 쌍)
    - Signature: 비밀키를 이용해 헤더에 정의된 알고리즘으로 서명
- Session과의 차이
    - 자체적으로 필요한 모든 정보를 지님
    - Session을 사용할 경우 Active User 수 만큼 Session을 저장->JWT사용이 유리
    - 유효기간이 남아 있는 정상적인 토큰에 대해 강제 만료 처리 어려움

[https://moonstal.tistory.com/159](https://moonstal.tistory.com/159)