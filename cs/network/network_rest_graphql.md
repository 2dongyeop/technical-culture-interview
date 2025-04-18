## REST vs GraphQL

<br/>

> **기본 개념**
>

- **REST (Representational State Transfer)**:
    - REST는 자원(Resource) 기반의 아키텍처 스타일로, 클라이언트가 서버에 요청을 보내면 서버는 요청된 자원에 대한 데이터를 반환합니다.
    - 각 자원은 고유한 URL을 가집니다.
- **GraphQL**:
    - GraphQL은 Facebook에서 개발한 쿼리 언어로, 클라이언트가 필요한 데이터를 **명시적으로 요청**할 수 있도록 합니다.
    - 단일 엔드포인트를 통해 요청하고, 서버는 클라이언트가 요청한 정확한 데이터만을 반환합니다.

<br/>

> **데이터 요청 방식**
>

- **REST**:
    - 요청은 일반적으로 **URL**(엔드포인트)로 이루어지며, 각 엔드포인트는 특정 리소스를 나타냅니다.
    - 예를 들어, `/users`는 사용자 데이터를 가져오고, `/products`는 제품 정보를 가져옵니다.
- **GraphQL**:
    - 하나의 엔드포인트에서 클라이언트가 원하는 **구체적인 데이터를 명시**할 수 있습니다.
    - 예를 들어, 클라이언트가 `name`, `age`만 필요하면, 서버에서 그 부분만 반환합니다.

<br/>

> **데이터 Over-fetching과 Under-fetching**
>

- **REST**:
    - 여러 엔드포인트를 호출해야 할 수 있고, 때때로 **Over-fetching**(필요하지 않은 데이터를 과다하게 요청) 또는 **Under-fetching**(필요한 데이터가 부족) 문제가 발생할 수
      있습니다.
- **GraphQL**:
    - 클라이언트가 요청한 **정확한 데이터만 반환**되므로 **Over-fetching**이나 **Under-fetching** 문제를 해결할 수 있습니다.
    - 클라이언트는 필요한 필드만 선택할 수 있기 때문입니다.

<br/>

> **버전 관리**
>

- **REST**:
    - **버전 관리**가 필요할 수 있습니다.
    - `/api/v1/users`와 `/api/v2/users`처럼 API 버전을 명시해야 할 경우가 많습니다.
- **GraphQL**:
    - GraphQL은 **버전 관리가 필요 없는** 아키텍처로 설계되었습니다.
    - 클라이언트가 필요한 필드를 요청하고, 새로운 필드가 추가되어도 클라이언트에서 명시적으로 요청하지 않으면 영향을 받지 않습니다.

<br/>

> **서버의 부담**
>

- **REST**:
    - 여러 엔드포인트와 각 엔드포인트에 대응하는 비즈니스 로직이 있어 서버 구현이 **복잡**
- **GraphQL**:
    - 하나의 엔드포인트로 다양한 데이터를 처리하기 때문에 서버에서 쿼리 최적화와 데이터 반환 처리에 **더 많은 리소스를 소모**할 수 있습니다.
    - 복잡한 쿼리가 서버에서 성능 문제를 일으킬 가능성도 있습니다.

<br/>

> **캐싱**
>

- **REST**: **HTTP 캐싱**을 활용할 수 있기 때문에, GET 요청에 대해 효과적으로 캐싱이 가능합니다.
- **GraphQL**: 캐싱이 상대적으로 **어려움**. 특히 쿼리가 동적으로 변할 수 있기 때문에, 세밀한 캐싱 전략이 필요합니다.

<br/>

- [관련 본인 게시글](https://velog.io/@dongvelop/Spring-Boot-GraphQL-%EC%86%8C%EA%B0%9C)