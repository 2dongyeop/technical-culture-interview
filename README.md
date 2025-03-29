# technical-interview

## 개요

전 직원이 7명인 스타트업에서 유일한 서버 개발자로 근무하다, 토스로 이직하기까지의 준비 과정을 정리했습니다.

여러 분야의 기본 개념들과 예상 면접 질문들로 이루어져 있으니, 아래 나열한 조건에 해당되시는 분들께 도움이 되셨으면 합니다.

- 첫 커리어를 시작하는 신입 & 이직을 준비하는 주니어 서버 개발자
- **서버 직군이 아니여도**, 컬쳐핏 면접을 앞두고 있는 개발자

<br/>

모두 행복하세요.

<br/>

## 목차

1. [기술면접 : CS 지식부터 프로젝트 기반 기술 면접까지](#기술-면접)
    - CS
        - [공통](#공통) , [Java](#1-1-java) , [Spring](#1-2-spring) , [JPA](#1-3-jpa) , [Database](#1-4-database) , [Network](#1-5-network) , [인프라/운영/안정성](#1-6-인프라운영안정성)
    - 이력서 프로젝트 기반 질문 (개인 맞춤)
2. [인성/컬쳐핏 면접 : 메타인지부터 조직문화 적합성까지](#인성-및-컬쳐핏-면접)
    - [인성 면접 준비 팁](#인성-면접-준비-팁)
        - [지원하는 회사의 인재상 및 비즈니스 알아보기](#지원하는-회사의-인재상-및-비즈니스-알아보기)
        - [가치관이 없으면 떨어진다.](#가치관이-없으면-떨어진다)
        - [미리 생각을 정리해놓아야 할 대표 질문 목록](#미리-생각을-정리해놓아야-할-대표-질문-목록)
    - [카테고리별 예상 질문 목록 세분화](#카테고리별-예상-질문-목록)
3. [면접 마지막에 물어보면 도움될 질문 목록](#면접-마지막에-물어보면-도움될-질문-목록)
4. [기타](#기타)
    - [이력서 작성 시 참고하면 좋을 자료들](#이력서-작성-시-참고하면-좋을-자료들)
    - [CS 지식 정리 시 참고하면 좋을 자료들](#cs-지식-정리-시-참고하면-좋을-자료들)
    - [인성 및 컬쳐핏 면접 준비 시 참고하면 좋을 자료들](#인성-및-컬쳐핏-면접-준비-시-참고하면-좋을-자료들)
    - [이직 준비시 멘탈 관리](#이직-준비시-멘탈-관리)

<br/>

# 기술 면접

## 1. CS

> 아래에 나올 CS 항목들은 필자가 "스스로 개념을 정리할 필요가 있는 항목들을 수집한 내용"입니다. <br/>
> 보시는 분들도 자신이 어느 파트가 공부해야 할 지 찾아보고, 필요한 항목들을 수집하여 면접을 준비하시면 좋을 것 같습니다. <br/>
> - [CS 지식 정리 시 참고하면 좋을 자료들](#cs-지식-정리-시-참고하면-좋을-자료들)

<br/>

### 공통

- 평소 기술 습득이나, 학습은 어떻게 하고 계신가요?
- 최근에 관심있게 읽으신 기술서적이나 학습한 내용은 무엇인가요?
- 기술블로그에 작성하신 내용 중, 가장 자신있는 내용을 저희에게 설명해주세요.
- [모든 개발자가 알아야 할 SOLID 원칙](https://tech.kakaobank.com/posts/2411-solid-truth-or-myths-for-developers/)
- [Spring boot에서의 싱글톤 패턴과 이외 디자인 패턴](cs/spring/spring_singleton.md)
    - [컴포지트 패턴을 알고 계신가요?](https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%EB%B3%B5%ED%95%A9%EC%B2%B4Composite-%ED%8C%A8%ED%84%B4-%EC%99%84%EB%B2%BD-%EB%A7%88%EC%8A%A4%ED%84%B0%ED%95%98%EA%B8%B0)
    - [전략 패턴에 대해 알고 계신가요?](https://victorydntmd.tistory.com/292)
    - [프록시 패턴에 대해 알고 계신가요?](https://inpa.tistory.com/entry/GOF-%F0%9F%92%A0-%ED%94%84%EB%A1%9D%EC%8B%9CProxy-%ED%8C%A8%ED%84%B4-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EB%B0%B0%EC%9B%8C%EB%B3%B4%EC%9E%90)
    - [**사용해보신 디자인 패턴에 사례를 설명해주시고, 장단점을 설명해주세요.**](cs/spring/template_pattern.md)
- [REST API vs gRPC](cs/network/network_rest_grpc.md)
- [REST vs GraphQL](cs/network/network_rest_graphql.md)
    - [REST API와 비교해서 GraphQL의 장단점을 설명해주세요.](cs/network/network_rest-graphql2.md)
    - [GraphQL을 도입하지 않았던 이유에 대해 설명해주세요.](cs/network/network_not_graphql.md)
- [Layered Architecture & Hexagonal Architecture](cs/spring/spring_architecture.md)
- [**Monolithic & MSA**](cs/spring/spring_monolithic_msa.md)
- [트랜잭션 관리가 어려운 분산 환경에서 일관성을 보장하기 위한 방법은 무엇인가요?](cs/spring/spring_atomic.md)

### 1-1. Java

- [**알아두면 좋을 JVM Option**](cs/java/jvm_options.md)
- [**JVM 옵션에서 Xmx, Xms를 동일하게 설정하는 이유**](cs/java/java_jvm_xmx_xms.md)
- [**Java의 Object 클래스의 Equals() 메서드와 HashCode() 메서드가 무슨 목적인지 설명해주세요.**](cs/java/java_equals_hascode.md)
- [자료구조 및 Java 컬렉션. with 동적 크기 조정](cs/java/java_%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0_%EC%BB%AC%EB%A0%89%EC%85%98.md)
- [추상클래스와 인터페이스의 차이](cs/java/java_%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4.md)
- [volatile 키워드는 무엇이고 언제 사용하나요?](cs/java/java_volatile.md)
- [synchronized 와 ReentrantLock](cs/java/java_synchronized_ReentrantLock.md)
- [**Synchronized는 어떤 내부 원리로 락을 동작시키는지 설명해주세요.**(뮤텍스락)](cs/java/how_synchronized.md)
- [**ConcurrentHashMap과 Atomic 클래스들은 내부적으로 어떻게 동시성 이슈를 해결했는지 아시나요?**(CAS)](cs/java/how_concurrenthashmap.md)
- [ThreadLocal 이란?](cs/java/java_threadlocal.md)
- [GC 별 특징 및 구조, 동작 과정](cs/java/java_gc.md)
- [비동기 처리 및 스레드 관리](cs/java/java_async.md)
- [스레드 상태에 대해 설명해주세요. 혹시 TIMED_WATING이랑 WAITING의 차이를 아시나요?](cs/java/thread_status.md)
- [JDK 8과 JDK 17, JDK 21의 주요 차이](cs/java/java_8_17_21.md)
- [**Virtual Threads**](cs/java/java_virtual_thread.md)
- [**OutOfMemoryError의 원인을 분석할 수 있나요?**](cs/java/java_oom.md)
- [JVM Cold Start 최적화를 위해 어떤 접근 방식을 사용했나요?](cs/java/java_cold_start.md)

### 1-2. Spring

- [Spring MVC와 디스패처 서블릿에 대해 설명해주세요.](cs/spring/spring_mvc.md)
- [Spring Bean과 생명주기](cs/spring/spring_bean_%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0.md)
- [의존성 주입 방식 비교](cs/spring/spring_%EC%9D%98%EC%A1%B4%EC%84%B1%EC%A3%BC%EC%9E%85.md)
- [Spring DI, IoC, AOP의 개념, **AOP의 내부 구현**](cs/spring/spring_di_ioc_aop.md)
- [Spring Boot 2.x와 3.x의 주요 차이점](cs/spring/spring_boot_2_3.md)
- [**OpenFeign 외에 다른 HTTP Client를 사용해보았는지? 다른 것들과 비교했을 때 불편한 점은 무엇이 있을까요?
  **](https://velog.io/@dongvelop/Spring-Cloud-OpenFeign-%EB%A9%94%EB%89%B4%EC%96%BC-%EC%A0%95%EB%A6%AC-with-Spring-REST-Clients)
- [마이크로서비스 간 통신에서 Feign Client를 사용시 주의점](cs/spring/spring_feign.md)
- [분산락(Distributed Lock) 개념 및 적용 방법](cs/spring/spring_lock.md)
- [Spring Cloud Config Server의 장단점](cs/spring/spring_cloud_config.md)
- [Circuit Breaker 패턴이 필요한 이유 & Spring Cloud Resilience4j 주요 기능](cs/spring/spring_circuit_breaker.md)
- [**Spring Cloud MSA 관련 모든것**](https://github.com/2dongyeop/spring-cloud-msa)

### 1-3. JPA

- [JPA는 무엇이며 어떤 특징/장점이 있는가?](cs/spring/spring_what_is_jpa.md)
- [Transaction이란 무엇인가? @Transaction 애너테이션의 주요 옵션에 대해 설명](cs/spring/spring_transaction.md)
- [영속성 컨텍스트란 무엇인가?](cs/spring/spring_context.md)
- [N+1 문제와 해결책](cs/spring/spring_jpa_n1.md)
    - 패치조인과 조인의 차이점을 알고 계신가요?
- [JPA OSIV(Open Session In View) 설정](cs/spring/spring_jpa_osiv.md)

### 1-4. Database

- [SQL vs NoSQL , 하이브리드 아키텍처 설계](cs/database/db_sql_nosql.md)
    - [**RDBMS는 어떤 이유로 NoSQL보다 읽기 성능이 좋을까요? 반대로, NoSQL은 어떤 이유로 쓰기 성능이 좋을까요?
      **](cs/database/why_rdb_better_than_nosql_and_why_nosql_better_than_rdb..md)
    - [**RDBMS에서 데이터가 많이 적재되면 무슨 문제가 발생하나요?**](cs/database/db_rdb_too_many_data.md)
- [인메모리 DB가 더 빠른 이유](cs/database/db_inmemory.md)
- [정규화/반정규화](cs/database/db_normalization.md)
- [**인덱스란?**](cs/database/db_index.md)
    - [**인덱스가 있음에도 성능이 더 느린 경우가 있다. 이에 대해 설명해보시오.**](cs/database/db_index_invalid.md)
    - [**LIKE 연산자가 인덱스를 사용하지 않는 이유**](cs/database/like_not_using_index.md)
    - [DB 인덱스가 어떤 자료구조로 이루어져 있어서, 성능을 향상시키나요?](cs/database/db_index_data_structure.md)
- [MySQL InnoDB의 기본 격리 수준이 어떻게 될까요?](cs/database/db_default_isolation_level.md)
- [Dirty Read, Non-Repeatable Read, Phantom Read, Gap Lock](cs/database/db_mysql_gaplock.md)
- [**MySQL MVCC 방식과 Undo Log에 대해 설명해주세요.**](cs/database/db_mysql_mvcc.md)
- [비관적 락과 낙관적 락에 대해 설명해주세요.](cs/database/db_lock.md)
- Redis는 메모리가 가득 찼을 때 어떻게 동작하나요?
- Redis를 스케일아웃 한다면 어떤 점들을 고려해야 하나요?

### 1-5. Network

- [TCP, UDP, HTTP, HTTPS](cs/network/network_tcp_udp_http_https.md)
- [쿠키(Cookie)와 세션(Session), JWT](cs/network/network_cookie_session_jwt.md)
- [HTTP 1.1, HTTP/2, HTTP/3](cs/network/network_http_1_2_3.md)
- [REST(Representational State Transfer)](cs/network/network_rest.md)
- [CORS(Cross-Origin Resource Sharing)](cs/network/network_cors.md)
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

> ### 안내
> 개인 프로젝트 경험 관련
> 내용은 [첨부한 이력서](https://github.com/2dongyeop/technical-interview/blob/main/resource/%EC%84%9C%EB%B2%84_%EA%B0%9C%EB%B0%9C%EC%9E%90_%EC%9D%B4%EB%8F%99%EC%97%BD_%EA%B2%BD%EB%A0%A5%EA%B8%B0%EC%88%A0%EC%84%9C.pdf)
> 를 기반으로 키워드를 추출하여 작성했습니다.
>
> 개인적인 경험이다보니 겹치는 내용은 없겠지만, **문제를 어떻게 파악하고 어떤 고민을 통해 어떻게 해결했는지 등을 참고하시는 데에 도움이 되었으면 합니다.**
>
>
> ### 답변 팁
> 1. 답변을 아래와 같은 순서로 진행하면 좋습니다. <br/>
     a. **진행 배경 → 기술 선택 및 이유 → 해결 방법 및 고민 내용 → 성과 혹은 아쉬운 점**
> 2. **어떤 역량을 평가하는 질문인지를 구분**하여 역량별 답변을 준비하는 것도 좋은 방법이라고 생각합니다. <br/>
     a. 의사결정 과정 / 문제 해결 능력 / 협업 경험

### 2-1. 공통

- [신기능 개발 시에 개발 프로세스와 각 단계별 역할을 설명해주세요.](project/common/develop_process.md)
- [**Retry 정책을 설계할 때 고려사항**](cs/spring/spring_retry.md)
- [여러 부하 테스트 툴(nGrinder, JMeter, k6, Locust) 중에서 nGrinder를 선택한 이유](project/common/load_test.md)
- [여러 APM 툴(Pinpoint, Datadog, Jaeger, New Relic, Zipkin) 중 Pinpoint을 선택한 이유](project/common/apm.md)
- 컴파일러를 모르는 사람이라고 가정하고, 저에게 JIT 컴파일러에 대해 설명해주세요. (상세 레벨 조절에 따른 성능 향상 이유)
- **프로젝트 경험 중, 가장 해결하기 어려웠거나 실패한 경험을 말해주세요. 그리고 어떻게 해결했으며, 해결하지 못했다면 어떤 대처를 해야할 지 말해주세요.**
- **근무하시는 동안 다양한 기술적 한계들을 맞이하실 수도 있을 것 같은데, 최선을 다해 어려움 & 기술적 한계를 극복한 사례가 있으신가요?**
- **프로젝트 중 실패 경험이 있으시다면 어떤게 있을까요? 만약 다시 돌아간다면 어떤 선택을 하실건가요?**
- **(성공적으로 마무리한 특정 프로젝트를 지정) 다시 돌아간다면, 어떤 점들을 더 개선할 수 있을까요?**
- [만약에 알림 서버를 구축한다고 하면, 컴포넌트별로 어떻게 아키텍처를 설계하실지 궁금한데, 그림으로 설명해주시겠어요?](https://github.com/Meet-Coder-Study/book-system-design-interview/blob/master/10%EC%9E%A5/%5B7%EC%A3%BC%EC%B0%A8%5D_10%EC%9E%A5_%EC%95%8C%EB%A6%BC%20%EC%8B%9C%EC%8A%A4%ED%85%9C_%EC%B5%9C%EC%A0%95%EA%B7%A0.md)

### 2-2. 문자 전송 클라이언트 변경

- [DB Agent 방식 vs API 방식 비교](project/2-2/db_agent_api.md)
- [OpenFeign과 Reactive Feign 비교. 비동기 전송이 목적일 때, WebClient를 제외한 이유는? 그리고 Reactive Feign의 단점.](project/2-2/reactive_feign.md)
- [문자 전송 성능이 200ms → 9ms로 개선된 과정은 어떻게 이루어졌나요?](project/2-2/reactive_feign_perform.md)
    - [**`@Async` 애너테이션이 완벽한 비동기가 아닌 이유에 대해 자세히 설명해주세요.**](project/2-2/why_async_not_full_async.md)
    - [Netty의 이벤트 루프(Event Loop) 모델에 대해 설명해주세요.](project/2-2/netty_event_loop.md)
    - [**논블로킹 형태의 클라이언트를 사용해서 성능을 개선하신 것 같은데.. 그럼 만약에 스레드풀을 충분히 많은 양으로 설정해놓았다면, 지금 개선하신 방식과 어떤 차이가 있을까요? 스레드풀의 크기가 클 경우에
      발생하는 문제점은 무엇일까요?**](project/2-2/non-blocking_threadpool.md)
    - 200ms, 9ms라고 말씀하신 Latency는 어떤 기준으로 어떻게 측정하신건가요?
- [**동기랑 비동기. 그리고 블로킹이랑 논블로킹에 대해 설명해주세요.**](project/2-2/sync_async_block_nonblock.md)
    - [**블로킹 함수를 사용하면서, 비동기로 개발할 수 있나요? 가능하다면, 예시를 들어 설명해주세요.**](project/2-2/blocking_async_combination.md)

### 2-3. 송아리에어 서브사용자 모니터링 기능 개발

- [SSE, WebSocket, MQTT의 동작 방식을 설명해주세요.](project/2-3/sse_websocket_mqtt.md)
- [실시간 알림임에도 REST 방식을 선택한 이유는 무엇인가요?](project/2-3/realtime_rest.md)
- JPA OSIV 옵션을 비활성화하지 않은 이유를 설명해주세요.

### 2-4. 서비스 복구 및 백업 프로세스 설립

- [서비스 복구/백업 프로세스 설립시 고려사항](project/2-4/recover.md)
- [AWS EC2 시작 템플릿 백업 시 기존 설정(인스턴스 사양, 네트워크, 보안그룹, EBS 사양) 유지 이유](project/2-4/launch_template_same_config.md)
- [AWS CLI 기술 선택 이유(AWS 생명주기관리자, Terraform을 사용하지 않은 이유)](project/2-4/aws_cli.md)
- [n8n을 선택하여 추가적인 헬스체크를 구축한 이유](project/2-4/n8n.md)
- [AMI 버저닝 관리를 통해 얻은 이점은 무엇인가요?](project/2-4/ami_versioning.md)
- [EC2 인스턴스 장애 상황에서 복구를 자동화한 방법은 무엇인가요?](project/2-4/recover_process.md)

### 2-5. 사내 온프레미스 서버 이관

- [mysqldump를 활용한 백업 자동화는 어떻게 구성했나요?](cs/database/db_mysqlbackup.md)
- [Nginx Brotli 압축 방식을 적용한 이유가 무엇인가요?](project/2-5/nginx_brotli.md)
- [프로젝트별 JDK 버전 상이 문제를 해결하기 위해 Docker 컨테이너 환경을 어떻게 구축/운영했나요?](project/2-5/docker_jdk.md)

### 2-6. 송아리 프리미엄(정기 구독 서비스) 개발

- [구독/결제 시스템에서 안정성 확보 및 상태 관리 전략을 어떻게 구성했나요?](project/2-6/subscription_stability.md)

### 2-7. AWS RDS 모니터링 시스템 구축

- [AWS RDS 모니터링 구축 시, AWS CloudWatch 대신 Percona rds_exporter를 선택한 이유](project/2-7/rds_monitoring.md)
- [AWS RDS 모니터링 시스템 구축 과정에서 문제점과 해결방법](project/2-7/rds_monitoring_troubleshooting.md)
- 모니터링할 때 관리 대상으로 여겨지는 주요 지표와 그 이유에 대해 설명해주세요.

### 2-8. 이미지 리사이징 처리 서버 구축

- [이미지 처리 서버 구축시, Thumbor를 택한 이유](project/2-8/why_thumbor.md)
- 리사이징이 일어나는 전체적인 동작 프로세스를 설명해주세요.
- AWS CloudFront나 S3 Presigned URL을 사용하지 않은 이유가 있나요?

### 2-9. 송아리당뇨 API Server 마이그레이션

- [모놀리식 아키텍처 구조의 프로젝트를 마이크로서비스로 전환한 이유](project/2-9/why_msa.md)
- MSA로 전환하며 겪었던 어려움과 해결 방안에 대해 설명해주세요.
- [대용량 데이터(약 60만 건) 조회 성능을 개선한 방법은 무엇인가요?](cs/database/db_60_perform.md)
- API 서버들 간, 혹은 외부 API 통신이 작용하고 있을 때, 서킷 브레이커는 어떻게 설정되어 있나요?
    - 만약, 서버가 스케일업 방식으로 이중화되어 있을 때, 외부 API에 문제가 생긴 상황에서 모든 서버들의 서킷브레이커 상태를 동기화하려면 어떻게 해야 할까요?
- DB도 개별 DB로 분리를 하셨나요? 단일 DB와 개별 DB의 운영 방식에 대한 차이를 알고 계신가요?
- 아키텍처는 어떤 것을 사용하고 계신가요? 비즈니스 로직은 (서비스, 도메인) 중 어디에 작성하고 계신가요? 해당 방법의 장단점과 연관지어 이유를 설명해주세요.

### 2-10. 평가 역량별 예상 질문 구분 예시

위에서 나온 키워드 질문들을 **평가 역량별**로 그룹핑한 예시입니다.

<details>
<summary><strong>의사결정 과정</strong></summary>

- API 서버를 모놀리식에서 MSA로 전환할 때, 공통 라이브러리를 만들기로 결정한 이유와 과정은?
- JDK 21, Spring Boot 3.4, Spring Cloud 2024.0으로 마이그레이션을 준비하면서 가장 중요하게 고려한 요소는?
- APM 도구를 비교/분석할 때 최종적으로 선택한 기준과 그 과정에서 팀과 어떻게 합의했는가?
- EC2의 Launch Template 업데이트를 자동화할 때, 어떤 전략을 선택했으며 그 선택이 가져온 장점과 단점은?
- Google Play 및 Apple App Store의 구독 결제 상태를 통합 정의할 때, 기존 방식과의 차별점 및 최종 모델을 선택한 기준은?

</details>

<details>
<summary><strong>문제 해결 능력(겪은 어려움과 해결 방법)</strong></summary>

- Pinpoint APM을 JDK 8 → JDK 17 환경으로 업그레이드할 때 가장 큰 기술적 문제는 무엇이었고, 이를 어떻게 해결했는가?
- Prometheus 기반 모니터링을 설정할 때 예상치 못한 장애나 데이터 수집 문제를 경험한 적이 있는가? 어떻게 해결했는가?
- Spring Boot 기반 GraphQL을 도입할 때 발생했던 주요 문제는 무엇이었고, 이를 어떻게 극복했는가?
- 대규모 성능 테스트를 진행할 때 JMeter, Gatling, k6, Locust 중 특정 도구를 선택해야 했을 때 어떤 문제가 있었고, 어떻게 해결했는가?
- AWS RDS(MySQL 8.0) 모니터링을 rds_exporter로 구축할 때 성능 최적화와 관련된 어려움이 있었나? 어떻게 해결했는가?

</details>

<details>
<summary><strong>협업 경험</strong></summary>

- 모놀리식 API 서버를 MSA로 전환하면서 프론트엔드, 데이터 엔지니어 팀과의 협업은 어떻게 진행했는가?
- APM 시스템(Pinpoint) 도입 후, 개발팀/운영팀과 데이터를 공유하거나 활용할 때 어떤 협업이 필요했으며, 어떻게 조율했는가?
- 구독 결제 시스템 개발 시, Google/Apple 정책 변경과 관련하여 비즈니스 팀과 협업한 경험이 있는가? 어떻게 소통했는가?
- 대규모 성능 테스트를 진행할 때 다른 개발자나 QA 팀과 어떻게 협업하여 효율성을 높였는가?
- 내부 기술 발표를 15회 진행하면서, 발표 주제 선정과 피드백 반영 과정에서 팀원들과 어떻게 협력했는가?

</details>


<br/>

# 인성 및 컬쳐핏 면접

> ### 답변 팁
>
> - 구체적인 경험을 포함하면 설득력이 높아집니다.
> - **STAR 기법**(상황, 과제, 행동, 결과)을 활용하면 논리적인 답변 구성이 가능합니다.
> - 면접을 보러 가는 회사 혹은 팀에서 운영하는 서비스에 대해서 알아가는 것도 중요합니다. 관심도가 영향을 미칠 수 있다고 생각해요.

## 인성 면접 준비 팁

<br/>

### 지원하는 회사의 인재상 및 비즈니스 알아보기

> 관심이 있어야, 이 회사에 입사하여 어떤 기여를 할 수 있을 지 기대하는 바를 말할 수 있음.

1. 지원하는 회사 홈페이지에서 지향하는 인재상 파악하기
2. 해당 기업의 일하는 방식/원칙 찾아보기
    - e.g. 토스의 경우 : "자율"과 "책임"을 중요시.
3. 채용 공고 검토하기(맡게될 업무, 지원자격, 우대사항 등)
4. 해당 기업의 뉴스 기사를 통해 사업 현황 파악하기
5. 해당 기업의 최근 투자 현황과 경쟁 업체들의 현황 파악하기
6. 링크드인 > 해당 기업 검색 > 사람들 프로필을 통해 어떤 기술스택으로, 어떤 프로젝트를 진행했는지 파악하기
7. 파악한 프로젝트의 소개/기술 중 주요 키워드를 추출하여 관련 기술블로그 아티클 읽기

<br/>

### 가치관이 없으면 떨어진다.

- 가치관을 통해 지금까지 일할 때(혹은 살아올 때) 어떤 기준을 가지고 판단을 내리고, 행위를 하는지 설명이 가능
- 자신이 우선시하는 특정 가치를 정하여 면접 캐릭터를 준비하면 좋음.
    - 일관성, 속도, 완벽함, 고객지향, 장기성장, 안정성 등등
- 그리고 자신의 가치관을 증명하기 위한 사례를 반드시 함께 말하기

<br/>

### 미리 생각을 정리해놓아야 할 대표 질문 목록

1. 이전에 경험했던 조직문화 중 가장 잘 맞았던 조직문화 & 잘 맞지 않았던 조직 문화는 무엇인가요?
    - **잘 맞았던 조직 문화 : 지원하는 회사의 문화와 유사한 경험을 강조**
    - **잘 맞지 않았던 조직 문화 : 지원하는 회사의 문화와 반대되는 경험을 말하고, 이를 성장 기회로 삼았다는 점을 강조**
2. 우리 회사에 입사한다면 조직문화와 일하는 방식 측면에서 가장 기대되는 점은 무엇인가요?
    - **지원하는 회사의 문화와 연결 & 기존 경험과 비교하여 차별점을 부각**
    - **단순한 기대가 아니라, 구체적인 성장 기회와 연결**
3. 주어진 업무 범위와 가이드를 넘어서 공동의 목표를 위해 스스로 주도적으로 기획하고 실행해 본 사례를 말씀해주세요.
    - **주어진 역할을 넘어서 자율적으로 기획하고 실행한 사례를 나열**
    - **단순히 기술적인 기여 뿐만 아니라, 비즈니스 성과로 연결되는지 검토**
4. 팀 내/외부의 사람들로부터 협업을 원활하게 이끌어내서, 성과를 창출한 사례를 말씀해주세요.
    - 근본적인 공동의 목표(문제)를 파악하고, 이를 해결한 사례를 제시
5. 어떤 분들과 함께할 때 가장 즐겁고 헌신적으로 일할 수 있나요?
6. 같이 일하고 싶은 & 일하기 싫은 개발자는 어떤 유형인가요?
    - **단순한 호불호가 아니라, "어떤 동료와 함께할 때 최고의 성과를 낼 수 있는지" 설명하도록 연결**
7. 자신의 성격 장점과 단점은 무엇이고, 이를 보완하기 위해 어떻게 노력하고 계신가요?
    - **강점은 어떻게 업무에 도움이 되는지**
    - **단점을 개선하기 위해 노력에서 나온 결과나 경험을 함께 설명**
    - **자기 인식이 높은 점이 포인트. 이로 인해 평소 삶의나 일의 방식으로 연결되기 때문.**
8. 회사/인생에서의 실패/성공 경험에 대해 말씀해주세요.
    - **"실패와 성공을 통해 무엇을 배웠는가"를 강조**
    - **특히 개인의 성장과 태도 변화를 보여주어도 좋음.**
        - 실패를 남 탓하지 않고, 본인의 판단 실수를 인정하는 태도 등..
9. 실패했던 프로젝트를 다시 하게 된다면 어떻게 성공하도록 시도할 것인가요?
10. 업무를 진행하는데 있어서 동료들과 소통은 어떤방식으로 하시나요?
    문제가 있다면 바로 직접적으로 말하시는 편인가요?
    - **피드백 문화에 대한 개인적인 견해를 노출**
    - **래디컬 캔도어 (Radical Candor) 검색해보기**
11. 주변 사람들에게 받았던 긍정적 혹은 부정적인 피드백은 무엇인가요?
    - **본인이 주요하게 생각하는 가치를 강조할 수 있도록 긍정적 피드백을 어필(e.g. 자기주도적인 성장 태도)**
    - **부정적인 피드백을 받고, 수용할 줄 아며 개선하려는 노력을 함께 말할 것**
12. 평소 스트레스를 받는 요인이 있다면, 어떤 것들인가요?
    - 스트레스 관리 능력과 휴식의 중요성을 강조 → 더 나은 업무 성과로 이어지도록

<br/>

## 카테고리별 예상 질문 목록

### 지원 동기

- 짧은 자기소개
- 지원 동기
    - [진태양님 블로그 - 모든 회사에 어필 할 수 있는 지원 동기와 목표설정 방법](https://dataportal.kr/%EB%AA%A8%EB%93%A0-%ED%9A%8C%EC%82%AC%EC%97%90-%EC%96%B4%ED%95%84-%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EC%A7%80%EC%9B%90-%EB%8F%99%EA%B8%B0%EC%99%80-%EB%AA%A9%ED%91%9C%EC%84%A4%EC%A0%95-%EB%B0%A9%EB%B2%95/)
- 저희 회사에 대해 알고 계신 것이 있으실까요? (자사 서비스 이용)
- 현재 회사(혹은 이전 직장)를 이직하려는 이유는 무엇인가요?
- 우리 회사에서 어떤 기여를 할 수 있을 것 같나요?

### 메타인지

- 성격이 외향적인지 내향적인지?
- 주변 사람들은 나를 어떤 사람으로 생각하는지?
- 본인의 강점과 약점은 무엇이라고 생각하나요?
- 본인이 주도적으로 진행한 프로젝트가 있다면 소개해주세요.
- 예상보다 성과가 좋지 않았던 경험이 있다면? 어떻게 대처했나요?
- 가장 최근에 배운 새로운 기술이나 개념은 무엇인가요?
- 자신이 성장했다고 느낀 순간은 언제인가요?

### 조직 문화 적합성

- 이상적으로 생각하는 조직/개발 문화
- 조직 문화에 적응하는 나만의 방법이 있는지
- 팀 내에서 커뮤니케이션할 때 가장 중요하게 생각하는 것은?
- 코드 리뷰나 피드백을 받을 때, 또는 줄 때 중요하게 여기는 점은?
- **같이 일하고 싶은 동료 유형과 같이 일하기 싫은 동료 유형**
    - **원하는 동료 = "어떤 환경에서 잘 협업하는지"에 중점을 두기**
    - e.g. "서로 피드백을 주고받으며 개선해 나가며 성장할 수 있는 동료들과 일하고 싶습니다."
- 협업 중 의견 충돌이 발생했을 때 어떻게 해결하는 편인가요?
- 개발자로서 성장하기 위해 동료에게 기대하는 것이 있나요?
- **스스로 어떤 동료가 되고 싶으신가요?**
    - **자신의 개발자로써의 성장 방향을 녹이기**
    - e.g. 제가 가진 경험을 공유하고, 저도 동료들에게 배우면서 함께 성장할 수 있는 환경을 만드는 개발자.
    - e.g. 단순히 주어진 개발만 하는 것이 아니라, 개발 과정에서 문제를 미리 발견하고, 해결 방안을 함께 고민하는 동료
        - "이 API 호출이 많아질 경우 성능 이슈가 발생할 가능성은 없을까?"
        - "이 데이터 구조가 향후 확장성을 고려했을 때 적절할까?"
- 팀원들에게 본인을 소개해달라고 하면, 어떤 동료라고 설명이 될 것 같으신가요?
- 다른 사람을 설득할 때, 주로 사용하는 접근 방식이 어떻게 되시나요? (e.g. 경험 기반, 데이터 기반, ...)
- 협업할 때 중요하게 생각하시는 것은 무엇인가요?
- 조직에서는 리더형이신가요? 아니면 팔로우형이신가요?
- Top-down 형식으로 일이 진행된 것 같은데, Bottom-up 형식으로 일하신 경험이 있으실까요? 혹은 Top-down 형식으로 일하면서 마주한 불편함이 있으실까요?

### 삶의 태도 및 가치관

- 주기적으로 회고를 진행하는지? 그렇다면 가장 기억에 남는 회고는?
- 장기적인 목표나 커리어 플랜이 있다면?
- 스트레스 해소 방법(취미, 주말)
- 삶에서 가장 중요하게 생각하는 가치
- 개발자로서 지속적으로 성장하기 위해 어떤 노력을 하고 있나요?
- 최근 가장 관심있게 접한 기술은 무엇인가요?
- 코드를 작성할 때, 어떤 부분을 가장 중요시 여기시나요? (e.g. 가독성, 성능 ..) 그리고 그 이유는 무엇인가요?
- 어떤 개발자가 되고 싶으신가요?
- 회사생활에서 ‘동료와의 화합, 나의 성장, 회사의 성장’ 중 어느 것이 가장 먼저인가요?
- 회사에서 받았던 피드백은 어떤게 기억에 남나요? 그리고 개선하셨나요?

<br/>

# 면접 마지막에 물어보면 도움될 질문 목록

### 업무 및 개발 프로세스 관련

- 신규 기능 개발 시, 업무 프로세스가 어떻게 되나요?
    - e.g.) Top-down / Bottom-up 인지, 일정 산출은 어떻게 진행되는지
- 배포 및 운영 프로세스는 어떻게 진행되나요?
    - CI/CD 및 배포 환경, 인프라 환경 유무 등
- 장애 대응(백업 및 복구) 체계는 어떻게 구성되어 있나요?

### 팀 및 조직 문화 관련

- 팀 구성이 어떻게 되어 있나요?
- 팀에서 사용하는 기술 스택이 어떻게 되나요?
- 팀원들(특히 서버측)의 평균 연차 및 근속 연수가 어떻게 되나요?
- 회사/팀 내 개발문화가 존재하나요? (코드리뷰, 1 on 1, 테크니컬 도큐먼트 작성, 장애 회고 등..)
- 평소 팀 분위기는 어떤가요? (잡담.. 회식.. 동아리.. 등등 유무)

### 커리어 성장 및 평가 관련

- 신입/경력 개발자의 온보딩 프로세스는 어떻게 진행되나요?
- 입사를 하게 되면 담당하게 될 업무는 무엇인가요?
- 개인의 성장과 역량 개발을 위한 피드백/평가 방식이 있나요?

### 회사 및 비즈니스 관련

- 레퍼런스 체크는 어떤 방식으로 진행되나요?
- **지원한 회사에 스페시픽한 질문** 추가하기

<br/>

# 기타

### 이력서 작성 시 참고하면 좋을 자료들

> 주변 선배나 혹은 커피챗을 통해 작성한 이력서를 피드백 받아보세요. 쑥스러워도 반드시 필요한 과정입니다.

- [진태양님](https://resume.dataportal.kr/)
- [요우님](https://resume.yowu.dev/)
- [Wonny | 데이터로 일하는 개발자 (Public)](https://www.notion.so/Wonny-Public-c2f8051bfb574f349406a30d2bc71a45?pvs=21)
- [이동욱님](https://jojoldu.github.io/)
- [아웃사이더님](https://blog.outsider.ne.kr/1234)

### CS 지식 정리 시 참고하면 좋을 자료들

- [남준이형 TIL](https://github.com/namjunemy/TIL)
- [본인 TIL](https://github.com/2dongyeop/TIL)
- [cheese10yun님 TIL](https://github.com/cheese10yun/TIL)
- [정신차려 이 각박한 세상속에서](https://www.notion.so/f8114c9e2c774eccaca509f9618b7115?pvs=21)
- [backtony/SW-Maestro-gjgs의 Tech 문서](https://github.com/backtony/SW-Maestro-gjgs/blob/master/TECH.md#-%EC%99%9C-%EC%9D%B4-%EA%B8%B0%EC%88%A0%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%96%88%EB%8A%94%EA%B0%80-)
- [신입 백엔드 면접 질문 Ver. 2.0.7](https://velog.io/@yukina1418/%EC%B5%9C%EA%B7%BC-%EB%A9%B4%EC%A0%91%EC%9D%84-%EB%8B%A4%EB%8B%88%EB%A9%B4%EC%84%9C-%EB%B0%9B%EC%95%98%EB%8D%98-%EC%A7%88%EB%AC%B8%EB%93%A4)
- [신입 개발자 기술면접 질문 모음](https://javanewbie.tistory.com/48)
- [시스템 설계 면접 팁1](https://brunch.co.kr/@jihyun-um/43)
- [시스템 설계 면접 팁2](https://deveric.tistory.com/105)
- [규글님](https://github.com/gyoogle/tech-interview-for-developer)
- [NKLCWDT/CS](https://github.com/NKLCWDT/cs)
- [한재엽님](https://github.com/JaeYeopHan/Interview_Question_for_Beginner)
- [WeareSoft/tech-interview](https://github.com/WeareSoft/tech-interview)
- [VSfe님](https://github.com/VSFe/Tech-Interview?tab=readme-ov-file)

### 인성 및 컬쳐핏 면접 준비 시 참고하면 좋을 자료들

- [예시와 함께 보는 컬쳐핏 면접 실수 3가지](https://www.youtube.com/watch?v=H2FwDFdD230)

### 이직 준비시 멘탈 관리

- [바다쓰기님 : 나의 첫번째 이직 회고, 5개월 간의 기록](https://xrabcde.github.io/moving-retrospection/)
- [강승현님 : 퇴사를 고민하는 주니어에게,](https://imksh.com/128)
- [최홍희님 : 카카오페이 경력 공채 합격 후기](https://vvshinevv.tistory.com/108)
- 카펀님
    - [세상은 넓고 잘하고 열심히 하는 사람은 많다.](https://vvshinevv.tistory.com/80)
    - [카카오페이 백엔드 개발자 경력 이직기](https://katfun.tistory.com/220)
- [태태태님 : 그런 개발자로 괜찮은가 - 취업편](https://taetaetae.github.io/posts/a-good-developer-in-terms-of-employment/)
- [재호님 : 수비수 개발자](https://jeho.page/essay/2024/08/08/defense-fun.html)
- [zzsza님 : 커리어 고민 상담을 하면서 많이 받은 고민 모음과 제 생각들](https://zzsza.github.io/diary/2025/02/16/career-advice/)
- [이호승님 : 좋은 개발팀을 만드는데 도움이 되는 자료](https://github.com/leehosung/awesome-devteam)
- [Greg Lee님 : 개발자 기술 면접](https://medium.com/@greg.shiny82/%EA%B0%9C%EB%B0%9C%EC%9E%90-%EA%B8%B0%EC%88%A0-%EB%A9%B4%EC%A0%91-144a1fe28ca4)
- [이직, 퇴사 체크리스트](https://velog.io/@hyperperi/%EC%9D%B4%EC%A7%81%ED%87%B4%EC%82%AC-%EC%B2%B4%ED%81%AC%EB%A6%AC%EC%8A%A4%ED%8A%B8)


