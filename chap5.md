## OAuth 2.0 Client

### 스프링 시큐리티와 OAuth 2.0
- `Spring Security Oauth Project` 는 `deprecated`되어 현재는 업데이트 되지 않고 있다.
- `Spring security`팀은 `Authorization server(인증서버)`를 지원하지 않는다고 발표했다.

| Spring Security Oauth Project |     | Spring Security 5 |
|-------------------------------|-----|-------------------|
| Client Support                |     | Client Support    |
| Resource Server               | ->  | Resource Server   |
| Authorization Server          |     |                   |

- `인증서버`를 지원하지 않는 대신 새로운 인증서버인 `spring authorization server` 를 제공하게 된다.

### OAuth 2.0 Client 소개
- 인가서버 및 리소스 서버와의 통신을 담당하는 클라이언트의 기능을 `필터 기반`으로 구현한 모듈
- OAuth 2.0 인증 및 리소스 접근 권한, 인가서버 엔드 포인트 통신 등의 구현이 가능, 확장이 용이하다.

#### OAuth 2.0 Login
- 외부 OAuth 2.0 Provider 나 OpenID Connect 1.0 Provider 계정으로 로그인 할 수 있는 기능을 제공한다.
- 구글계정, 깃허브 계정 로그인 기능을 OAuth 2.0 로그인을 구현해 사용할 수 있도록 지원한다.
- Authorization Code 방식을 사용한다.

#### OAuth 2.0 Client
- OAuth 2.0 인가 프레임워크에 정의된 클라이언트 역할을 지원한다.
- 인가 서버의 권한 구여 유형에 따른 엔드 포인트와 직접 통신할 수 있는 API를 제공한다.
  - Client Credentials
  - Resource Owner Password Credentials
  - Refresh Token
- 리소스 서버의 보호자원 접근에 대한 연동 모듈을 구현 할 수 있다.


#### 의존성
```groovy
implementation 'org.springframework.boot:spring-boot-starter-oauth2-client'
```