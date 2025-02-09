## Spring boot는 싱글톤 패턴으로 돌아가는데 이에 대해 설명하고, 싱글톤 패턴이 무엇이며 다른 알고 있는 패턴이 있는가?

<br/>

> Spring Boot에서 Bean은 기본적으로 **싱글톤(Singleton) 패턴**으로 관리된다.
>

- **싱글톤 패턴**이란 **애플리케이션 내에서 특정 객체를 단 하나만 생성하여 공유하는 디자인 패턴**입니다.
- Spring Boot의 **IoC 컨테이너(ApplicationContext)는 기본적으로 모든 Bean을 싱글톤으로 관리**하여 불필요한 객체 생성을 방지하고, **메모리 효율성을 높임**.
- Bean은 내부적으로 싱글톤 스코프 (`@Scope("singleton")`)로 선언되어 있음.

<br/>

> 기타 다른 디자인 패턴
>

- **Factory Pattern (팩토리 패턴)**
    - 객체 생성 로직을 캡슐화하여 클라이언트 코드가 직접 `new`를 사용하지 않도록 하는 패턴
- Observer Pattern (옵저버 패턴)
    - 특정 객체의 상태 변경을 감지하고 자동으로 알림을 보내는 패턴
    - e.g) **Spring의 EventListener 기능**