# OAuth 2.0 Fundamentals

-----

1. OAuth = Open + Authorization(인가)
   - 인가 : 권한을 부여한다.
   - OAuth 2.0 Authorization Framework(RFC 6749)
   - 사용자가 속한 사이트의 보호된 자원(사용자 정보)에 대해 어플리케이션의 접근을 허용하도록 승인하는 것

   
2. Delegated authorization framework - 위임 인가 프레임워크
   - 어플리케이션이 사용자의 데이터에 접근하도록 권한을 부여한다.
   - 즉, 인가 서버가 어플리케이션이 권한을 부여한다.

### 이전방식
- 직접 아이디와 패스워드를 입력하여 로그인함으로 계정정보가 노출되어 보안에 취약하다.
- OAuth를 사용하면 계정정보가 노출될 필요 없이 로그인 및 사용자가 허용한 정보에 접근이 가능하다.
- 사용자 정보의 접근 권한을 주는 주체는 사용자가 된다.
