# Oauth 2.0 Client Fundamentals

## OAuth2ClientProperties

### 클라이언트 권한 부여 요청 시작
1. 클라이언트가 인가서버로 권한 부여 요청을 하거나 토큰 요청을 할 경우 클라이언트 정보 및 엔드포인트 정보를 참조하여 전달.
2. `application.yml` 환경설정 파일에 클라이언트 설정과 인가서버 엔트포인트 설정을 한다.
3. `application.yml` 파일에 있는 정보들이 `OAuth2ClientProperties` 클래스에 바인딩된다.
4. 바인딩된 정보를 통해 `ClientRegistration` 클래스 필드에 저장된다.
5. `ClientRegistration`를 참조하여 권한부여 요청을 위한 매개변수를 구성하고 인가서버와 통신한다.


### application.yml
```yaml
server:
  port: 8081

spring:
  security:
    oauth2:
      client:
        registration: # 클라이언트 설정
          keycloak:
            clientId: oauth2-client-app
            clientSecret: dXf021lMWuZ9kZafqxZn230MvVEdROIo
            clientName: oauth2-client-app
            authorizationGrantType: authorization_code
            scope: openid,profile
            clientAuthenticationMethod: client_secret_basic
            redirectUri: http://localhost:8081/client # keycloak에 등록해줘야함
            provider: keycloak

        provider: # 공급자 설정
          keycloak:
            issuerUri: http://localhost:8080/realms/oauth2
            authorizationUri: http://localhost:8080/realms/oauth2/protocol/openid-connect/auth
            jwkSetUri: http://localhost:8080/realms/oauth2/protocol/openid-connect/certs
            tokenUri: http://localhost:8080/realms/oauth2/protocol/openid-connect/token
            userInfoUri: http://localhost:8080/realms/oauth2/protocol/openid-connect/userinfo
            userNameAttribute: preferred_username
```

### OAuth2ClientProperties
![img.png](./image/img6_2.png)

- `Registration`은 인가 서버에 등록된 클라이언트 및 요청 파라미터 정보를 나타낸다.
- `Provider`는 공급자에게 제공하는 엔드포인트 등의 정보를 나타낸다.

## ClientRegistration
- `OAuth 2.0` 또는 `OIDC 1.0 Provider` 에서 클라이언트의 등록 정보를 나타낸다.
- `OIDC Provider`의 설정 엔드포인트나 인가 서버의 메타데이터 엔드포인트를 찾아 초기화 할 수 있다.
- `ClientRegistrations` 메서드를 사용하여 설정.
  - `ClientRegistration clientRegistration = ClientRegistrations.fromIssuerLocation(“https://idp.example.com/issuer”).build();`

![img.png](./image/img6_4.png)


### OAuth2Provider
- 글로벌한 서비스 제공자의 설정을 기본으로 제공한다.
- `Client ID` 와 `Client Secret`은 별도 `application.yml`에 작성해야한다.
- `yml`파일이 아닌 `Java Config`방식으로도 등록을 할 수 있음
- 위에서 제공되지 않는 공급자 정보는 수동으로 설정 해줘야 한다.

![img.png](./image/img6_3.png)
![img.png](./image/img6_5.png)

### ClientRegistrationRepository
- `ClientRegistrationRepository`은 `ClientRegistration` 저장소 역할을 한다.
- 인가 서버에 일차적으로 저장된 클라이언트 등록 정보의 일부를 검색하는 기능을 제공.
- `ApplicationContext`내 `Bean`으로 등록되서 의존성 주입을통해서 사용 할 수 있다.


- 이런식으로 `ClientRegistration` 클래스를 사용하여 `Bean`으로 생성 가능
![img.png](img6_6.png)