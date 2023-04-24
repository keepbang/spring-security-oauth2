## Oauth 2.0 Grant Type

-----

### 권한 부여 유형

- 클라이언트가 사용자를 대신해서 사용자의 승인하에 인가서버로부터 권한을 부여받는 것.

1. Authorization Code Grant Type
   - 권한 코드 부여 타입. 
   - 가장 보안에 안전한 유형.
2. Client Credentials Grant Type
   - 클라이언트 자격 증명 권한 부여 타입, 클라이언트 아이디와 클라이언트 시크릿만 존재하면 가능
   - 서버 애플리케이션에서 사용됨.(server to server)
3. Refresh Token Grant Type
   - Refresh 토큰으로 권한부여를 따로 하지 않고 새롭게 토큰을 발급 받을수 있는 타입.
   - Authorization Code Type 에서 지원.
4. PKCE-enhanced Authorization Code Grant Type 
   - Authorization Code Type과 비슷하지만 PKCE(Proof Key of Code Exchange)를 사용하여 좀 더 강화된 타입.
   - 코드를 발급 받을때 추가로 해쉬된 값을 전달해서 코드를 발급 받는다.
5. Implicit Grant Type <font color="red">***(deprecated)***</font>
   - 암시적 부여 타입, 공개 클라이언트 애플리케이션(개발자 도구로 스크립트 확인 가능).
   - 보안에 취약함.
6. Resource Owner Password Credentials Grant Type <font color="red">***(deprecated)***</font>
   - 사용자의 패스워드를 통해서 자격 증명을 부여받는 타입, 패스워드 노출 가능성 있음.
   - 보안에 취약함.


### 매개 변수 용어
- 클라이언트가 인가서버에게 요청을 할때 필요한 변수들.

  #### client_id
  - 인가서버에 등록된 클라이언트에 대해 생성된 고유 키
  #### client_secret
  - 인가서버에 등록된 특정 클라이언트의 비밀 값
  #### response_type
  - 애플리케이션이 권한 부여 코드 흐름을 시작하고 있음을 인증 서버에 알려준다.
  - code, token, id_token 이 있으며, token, id_token은 Implicit 권한 부여 유형에서 지원해야 한다.
  - callback url에 code와 token이 붙여서 나옴
  #### grant_type
  - 권한 부여 타입 지정
  #### redirect_uri
  - 사용자가 애플리케이션을 성공적으로 승인하면 권한 부여 서버가 사용자를 다시 애플리케이션으로 리다이렉션한다.
  - 토큰 요청의 redirect_uri 는 인증 코드를 생성할 때 사용된 redirect_uri 와 정획히 일치해야 한다.
  #### scope
  - 애플리케이션이 사용자 데이터에 접근하는 것을 제한하기 위해 사용된다.(profile, email)
  - 인가서버에 존재하는 scope를 사용해야 한다.
  - 특정 스코프로 제한된 권한 인가권을 발행함으로써 데이터 접근을 제한한다.
  #### state
  - 클라이언트가 인가서버에 요청을 보낼 때 임의의 문자열을 포함시켜 보내주고 승인 후 서버로부터 동일한 값이 반환되는지 확인해야 한다.
  - CSRF 공격을 방지하는데 사용된다.(위조 방지)
