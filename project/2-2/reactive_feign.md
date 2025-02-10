## OpenFeign과 Reactive Feign 비교. 비동기 전송이 목적일 때, WebClient를 제외한 이유는?

<br/>

> **OpenFeign vs. Reactive Feign 비교**
>

| 특징           | OpenFeign                                           | Reactive Feign                        |
|--------------|-----------------------------------------------------|---------------------------------------|
| **패러다임**     | 동기(Synchronous)                                     | 비동기(Asynchronous)                     |
| **기반 기술**    | `RestTemplate`(기본) 또는 `OkHttp`, `Apache HttpClient` | `Spring WebFlux` (Reactor 기반)         |
| **응답 처리 방식** | 요청이 완료될 때까지 블로킹                                     | `Mono<T>`, `Flux<T>`를 반환하여 논블로킹 방식 지원 |
| **적용 가능 환경** | 일반적인 Spring MVC 환경                                  | WebFlux 기반의 리액티브 시스템                  |
| **성능**       | 요청이 많아지면 스레드 증가로 인해 성능 저하 가능                        | 논블로킹 방식으로 적은 리소스로 높은 처리량 가능           |
| **주요 활용 사례** | 마이크로서비스 간 HTTP 클라이언트 통신(일반적인 REST API 호출)           | 대량의 병렬 요청이 필요한 경우 또는 WebFlux 기반 서비스   |

<br/>

> **비동기 전송 시 WebClient를 제외한 이유**
>

1. **Feign은 선언형 인터페이스 방식 제공**
    - Feign은 인터페이스에 어노테이션만 추가하면 구현체 없이 간단하게 HTTP 클라이언트를 생성할 수 있음.
    - WebClient는 `builder` 패턴을 사용하여 직접 HTTP 요청을 구성해야 하므로 Feign보다 코드가 길어질 수 있음.
2. **Feign은 Spring Cloud 환경과 잘 통합됨**
    - OpenFeign은 Spring Cloud와의 통합성이 뛰어나서 로드 밸런싱(`@LoadBalanced`), 서킷 브레이커(`Resilience4J`), 모니터링 등의 기능을 쉽게 적용할 수 있음.
    - WebClient를 사용할 경우 이러한 기능을 별도로 설정해야 하는 부담이 있음.
3. **Reactive Feign은 WebFlux와 같은 논블로킹 환경에서 자연스럽게 동작**
    - WebClient도 논블로킹이지만, Feign을 사용하면 기존 Feign 기반의 코드와 일관성을 유지하면서 비동기 방식으로 전환 가능함.
    - 이미 Feign을 사용하고 있는 프로젝트라면 WebClient로 전환하는 것보다 `Reactive Feign`을 활용하는 것이 더 쉬운 선택이 될 수 있음.