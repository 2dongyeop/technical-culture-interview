## Spring Boot 2.x와 3.x의 주요 차이점

1. **JDK 17 이상으로 업그레이드 필수**
    - **Spring Boot 2.x**: **JDK 8, 11, 17**을 지원
    - **Spring Boot 3.x**: **JDK 17 이상**만 지원
2. **`javax` → `jakarta` 패키지 변경으로 인한 코드 수정 필요**
    - **Spring Boot 3.x부터 Jakarta EE 9+ 기반으로 변경**
    - 기존 **`javax.*` 네임스페이스가 `jakarta.*`로 변경됨**
3. **Hibernate 6.x로 인한 JPA 설정 점검**
    - Spring Boot 3.x에서는 **Hibernate 6.x**을 사용
    - **쿼리 실행 방식 및 Dialect 변경**

        ```bash
        # Spring Boot 2.x
        spring.jpa.database-platform=org.hibernate.dialect.MySQL57Dialect
        
        # Spring Boot 3.x
        spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
        ```

4. **Spring Security 설정 방식 변경 확인**
    - Spring Boot 2.x에서는 `WebSecurityConfigurerAdapter`를 상속하여 보안 설정
    - Spring Boot 3.x에서는 **람다 기반 설정 방식이 기본값**으로 변경됨
5. **Micrometer 및 Observability 도입 검토**
    - **Spring Boot 2.x**: Micrometer는 주로 메트릭(Metrics)만 제공
    - **Spring Boot 3.x**: Micrometer에 **Tracing 기능 추가**
6. **GraalVM 네이티브 이미지 적용 검토 (서버리스 환경일 경우 유용)**
    - **Spring Boot 3.x에서는 GraalVM을 공식 지원**하여 **네이티브 실행 파일을 생성 가능**
    - **기존 JVM 기반보다 빠른 실행 속도**와 **낮은 메모리 사용량**을 제공