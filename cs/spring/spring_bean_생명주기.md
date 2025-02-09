## Spring Bean은 무엇이며, 생명주기는 어떻게 되는가?

<br/>

> Spring Bean 정의
>

**Spring IoC (Inversion of Control) 컨테이너**에 의해 관리되는 객체를 의미

주로 `@Component`, `@Service`, `@Repository`, `@Controller` 또는 `@Bean` 등을 사용하여 선언

<br/>

> 생명주기
>

**1) Bean 객체 생성**

- Spring 컨테이너가 `@ComponentScan` 또는 `@Bean` 메서드를 통해 Bean을 생성합니다.
- 컨테이너가 로딩될 때 인스턴스화됩니다.

**2) 의존성 주입 (Dependency Injection)**

- `@Autowired`, `@Value` 등을 통해 필요한 의존성을 주입받습니다.
- 이 단계에서 Setter Injection, Constructor Injection, Field Injection 등이 수행됩니다.

**3) 초기화 (Initialization)**

- Bean이 생성된 후 초기화 로직이 실행됩니다.
- 방법:
    - `@PostConstruct` (JDK 표준)
    - `InitializingBean` 인터페이스의 `afterPropertiesSet()` 메서드

**4) 소멸 (Destruction)**

- Bean이 소멸되기 전에 정리 작업이 수행됩니다.
- 방법:
    - `@PreDestroy` (JDK 표준)
    - `DisposableBean` 인터페이스의 `destroy()` 메서드