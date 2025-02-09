## REST(Representational State Transfer)

> **REST (Representational State Transfer)**
>

- **정의:**
    - REST는 **웹 서비스 아키텍처 스타일**의 하나로, **HTTP**를 기반으로 하여 **클라이언트와 서버 간의 상태 전이**를 추상화한 설계 원칙입니다.
    - REST는 웹의 특징인 **무상태성(Stateless), 클라이언트-서버 구조** 및 **자원의 표현**을 중심으로 합니다.
- **특징:**
    - **무상태성(Stateless):** 각 요청은 독립적으로 처리되며, 서버는 클라이언트의 상태를 저장하지 않음
    - **자원(Resource):** 모든 것은 자원(URI)으로 표현됩니다.
      예를 들어, `/users`는 사용자 목록, `/users/{id}`는 특정 사용자 자원
    - **표현(Representation):** 자원은 JSON, XML, HTML 등 다양한 형태로 클라이언트에 제공될 수 있음
    - **HTTP 메서드 사용:** REST는 HTTP 메서드를 활용하여 자원에 대해 CRUD 작업을 수행
    - **주소 지정:** 각 자원은 고유한 URI로 식별
- **예시 답변:**

  *"REST는 HTTP 기반의 아키텍처 스타일로, 자원(Resource)을 URI로 정의하고, HTTP 메서드를 사용하여 자원에 대한 CRUD 작업을 처리합니다. 각 요청은 독립적이며 서버는 클라이언트의 상태를
  저장하지 않습니다."*