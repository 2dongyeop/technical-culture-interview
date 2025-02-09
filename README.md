# technical-interview

기술 및 인성/컬쳐핏 면접 준비 자료

### 목차

작성 예정.

<br/>

# 기술 면접

## 1. CS

### 1-1. Java

- [자료구조 및 Java 컬렉션. with 동적 크기 조정](cs/java/java_%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0_%EC%BB%AC%EB%A0%89%EC%85%98.md)
- [추상클래스와 인터페이스의 차이](cs/java/java_%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4.md)
- [volatile 키워드는 무엇이고 언제 사용하나요?](cs/java/java_volatile.md)
- [synchronized 와 ReentrantLock](cs/java/java_synchronized_ReentrantLock.md)
- [GC 별 특징 및 구조, 동작 과정](cs/java/java_gc.md)
- [비동기 처리 및 스레드 관리](cs/java/java_async.md)
- [ThreadLocal](cs/java/java_threadlocal)
- [JDK 8과 JDK 17, JDK 21의 주요 차이](cs/java/java_8_17_21.md)
- [**Virtual Threads**](cs/java/java_virtual_thread.md)
- [**JVM 옵션에서 Xmx, Xms를 동일하게 설정하는 이유**](cs/java/java_jvm_xmx_xms.md)
- [**OutOfMemoryError의 원인을 분석할 수 있나요?**](cs/java/java_oom.md)
- [JVM Cold Start 최적화를 위해 어떤 접근 방식을 사용했나요?](cs/java/java_cold_start.md)

### 1-2. Spring

- [Spring Bean과 생명주기](cs/spring/spring_bean_%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0.md)
- [의존성 주입 방식 비교](cs/spring/spring_%EC%9D%98%EC%A1%B4%EC%84%B1%EC%A3%BC%EC%9E%85.md)
- [Spring DI, IoC, AOP](cs/spring/spring_di_ioc_aop.md)
- [Spring boot에서의 싱글톤 패턴과 이외 디자인 패턴](cs/spring/spring_singleton.md)
- [Spring Boot 2.x와 3.x의 주요 차이점](cs/spring/spring_boot_2_3.md)
- [Layered Architecture & Hexagonal Architecture](cs/spring/spring_architecture.md)
- [**Monolithic & MSA**](cs/spring/spring_monolithic_msa.md)
- [마이크로서비스 간 통신에서 Feign Client를 사용시 주의점](cs/spring/spring_feign.md)
- [**Retry 정책을 설계할 때 고려사항**](cs/spring/spring_retry.md)
- [분산락(Distributed Lock) 개념 및 적용 방법](cs/spring/spring_lock.md)
- [트랜잭션 관리가 어려운 분산 환경에서 일관성을 보장하기 위한 방법은 무엇인가요?](cs/spring/spring_atomic.md)

### 1-3. JPA

- [JPA는 무엇이며 어떤 특징/장점이 있는가?](cs/spring/spring_what_is_jpa.md)
- [Transaction이란 무엇인가? @Transaction 애너테이션의 주요 옵션에 대해 설명](cs/spring/spring_transaction.md)
- [영속성 컨텍스트란 무엇인가?](cs/spring/spring_context.md)
- [N+1 문제와 해결책](cs/spring/spring_jpa_n1.md)
- [JPA OSIV(Open Session In View) 설정](cs/spring/spring_jpa_osiv.md)

### 1-4. Database

- [SQL vs NoSQL , 하이브리드 아키텍처 설계](cs/database/db_sql_nosql.md)
- [인덱스란?](cs/database/db_index.md)
- [정규화/반정규화](cs/database/db_normalization.md)
- [인메모리 DB가 더 빠른 이유](cs/database/db_inmemory.md)
- [**인덱스가 있음에도 성능이 더 느린 경우가 있다. 이에 대해 설명해보시오.**](cs/database/db_index_invalid.md)
- [mysqldump를 활용한 백업 자동화는 어떻게 구성했나요?](cs/database/db_mysqlbackup.md)

### 1-5. Network

- [TCP, UDP, HTTP, HTTPS](cs/network/network_tcp_udp_http_https.md)
- [쿠키(Cookie)와 세션(Session), JWT](cs/network/network_cookie_session_jwt.md)
- [HTTP 1.1, HTTP/2, HTTP/3](cs/network/network_http_1_2_3.md)
- [REST(Representational State Transfer)](cs/network/network_rest.md)
- [CORS(Cross-Origin Resource Sharing)](cs/network/network_cors.md)
- [**REST API vs gRPC**](cs/network/network_rest_grpc.md)
- [**REST vs GraphQL**](cs/network/network_rest_graphql.md)
- [특정 요청의 응답 속도가 느려지는 원인은?](cs/network/network_slow_response.md)

### 1-6. 인프라/운영/안정성

- [**Linux 운영 명령어**](cs/infra/infra_linux_command.md)
- [온프레미스와 클라우드 비교](cs/infra/infra_onprem_cloud.md)
- [**모니터링 및 Alert 구축 시 고려사항**](cs/infra/infra_monitoring_alert.md)
- [**쿼리 성능 개선: 인덱싱 및 실행 계획 분석**](cs/database/db_performence.md)
- [부하 테스트 및 TPS 분석 시 고려사항](cs/infra/infra_load_test_consider.md)
- [APM 활용 방안](cs/infra/infra_apm.md)
- [배포 전략: 카나리, 블루-그린, 롤링 배포 비교](cs/infra/infra_deploy.md)

<br/>

## 2. 프로젝트 경험

### 2-1. 공통
- [여러 부하 테스트 툴(nGrinder, JMeter, k6, Locust) 중에서 nGrinder를 선택한 이유](project/common/load_test.md)
- [테스트 코드 작성 원칙 및 전략이 있는지?]

### 당뇨

- [대용량 데이터(약 60만 건) 조회 성능을 개선한 방법은 무엇인가요?](cs/database/db_60_perform.md)

<br/>

## 인성 면접

업로드 예정