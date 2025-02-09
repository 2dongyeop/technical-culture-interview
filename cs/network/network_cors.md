## CORS(Cross-Origin Resource Sharing)

> **정의**
>

- CORS는 **Cross-Origin Resource Sharing**의 약자
- 다른 출처(origin)에서 제공하는 리소스를 **웹 브라우저에서 안전하게 요청하고 사용할 수 있도록 허용하는 보안 메커니즘**입니다.
- 기본적으로 **웹 브라우저의 보안 정책인 Same-Origin Policy**에 의해, 한 도메인에서 로드된 웹 페이지는 다른 도메인의 리소스를 접근할 수 없습니다.
- CORS는 이러한 제약을 완화하는 방법을 제공합니다.

<br/>

> **CORS 동작 방식:**
>

- **Preflight Request:**
    - 브라우저가 실제 요청을 보내기 전에 **OPTIONS 요청**을 서버에 보내 **해당 요청을 허용할 수 있는지 확인**합니다.
    - 이 과정은 **Custom Headers**나 **HTTP 메서드(예: PUT, DELETE 등)**를 사용할 때 발생합니다.
- **Access-Control-Allow-Origin 헤더:**
    - 서버는 응답에 `Access-Control-Allow-Origin` 헤더를 추가하여 **어떤 도메인이 자원에 접근할 수 있는지** 명시합니다.
        - `Access-Control-Allow-Origin: *` (모든 도메인 허용)
        - `Access-Control-Allow-Origin: https://example.com` (특정 도메인 허용)