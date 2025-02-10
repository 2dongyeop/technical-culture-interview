# technical-interview

기술 및 인성/컬쳐핏 면접 준비 자료

### 목차

#### [기술 면접](#기술-면접)

1. [CS](#1-cs)
    - [1-1. Java](#1-1-java)
    - [1-2. Spring](#1-2-spring)
    - [1-3. JPA](#1-3-jpa)
    - [1-4. Database](#1-4-database)
    - [1-5. Network](#1-5-network)
    - [1-6. 인프라/운영/안정성](#1-6-인프라운영안정성)

2. [프로젝트 경험](#2-프로젝트-경험)

    - [2-1. 공통](#2-1-공통)
    - [2-2. 문자 전송 클라이언트 변경](#2-2-문자-전송-클라이언트-변경)
    - [2-3. 송아리에어 서브사용자 모니터링 기능 개발](#2-3-송아리에어-서브사용자-모니터링-기능-개발)
    - [2-4. 서비스 복구 및 백업 프로세스 설립](#2-4-서비스-복구-및-백업-프로세스-설립)
    - [2-5. 사내 온프레미스 서버 이관](#2-5-사내-온프레미스-서버-이관)
    - [2-6. 송아리 프리미엄정기 구독 서비스 개발](#2-6-송아리-프리미엄정기-구독-서비스-개발)
    - [2-7. AWS RDS 모니터링 시스템 구축](#2-7-aws-rds-모니터링-시스템-구축)
    - [2-8. 이미지 리사이징 처리 서버 구축](#2-8-이미지-리사이징-처리-서버-구축)
    - [2-9. 송아리당뇨 API Server 마이그레이션](#2-9-송아리당뇨-api-server-마이그레이션)

#### [인성 면접](#인성-면접)

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
- [분산락(Distributed Lock) 개념 및 적용 방법](cs/spring/spring_lock.md)
- [트랜잭션 관리가 어려운 분산 환경에서 일관성을 보장하기 위한 방법은 무엇인가요?](cs/spring/spring_atomic.md)
- [Spring Cloud Config Server의 장단점](cs/spring/spring_cloud_config.md)
- [Circuit Breaker 패턴이 필요한 이유 & Spring Cloud Resilience4j 주요 기능](cs/spring/spring_circuit_breaker.md)
- [Spring Cloud MSA 관련 모든것](https://github.com/2dongyeop/spring-cloud-msa)

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

> ### 안내
> 개인 프로젝트 경험 관련
>
내용은 [첨부한 이력서]((resource/%E1%84%89%E1%85%A5%E1%84%87%E1%85%A5_%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1_%E1%84%8B%E1%85%B5%E1%84%83%E1%85%A9%E1%86%BC%E1%84%8B%E1%85%A7%E1%86%B8_%E1%84%80%E1%85%A7%E1%86%BC%E1%84%85%E1%85%A7%E1%86%A8%E1%84%80%E1%85%B5%E1%84%89%E1%85%AE%E1%86%AF%E1%84%89%E1%85%A5.pdf))
> 를 기반으로 키워드를 추출하여 작성했습니다. 개인 경험이다보니 겹치는 내용이 없을 지도 모릅니다.
>
> 어느 문제를 어떻게 접근했는지 등을 참고하시는 데에 도움이 되었으면 합니다.
>
>
> ### 답변 팁
> 1. 답변을 아래와 같은 순서로 진행하면 좋습니다. <br/>
     a. **진행 배경 → 기술 선택 및 이유 → 해결 방법 및 고민 내용 → 성과 혹은 아쉬운 점**
> 2. **어떤 역량을 평가하는 질문인지를 구분**하여 역량별 답변을 준비하는 것도 좋은 방법입니다. <br/>
     a. 의사결정 과정 / 문제 해결 능력 / 협업 경험

### 2-1. 공통

- [신기능 개발 시에 개발 프로세스와 각 단계별 역할을 설명해주세요.](project/common/develop_process.md)
- [여러 부하 테스트 툴(nGrinder, JMeter, k6, Locust) 중에서 nGrinder를 선택한 이유](project/common/load_test.md)
- [여러 APM 툴(Pinpoint, Datadog, Jaeger, New Relic, Zipkin) 중 Pinpoint을 선택한 이유](project/common/apm.md)
- [테스트 코드 작성 원칙 및 전략이 있는지?](project/common/test_code.md)
- [**Retry 정책을 설계할 때 고려사항**](cs/spring/spring_retry.md)

### 2-2. 문자 전송 클라이언트 변경

- [DB Agent 방식 vs API 방식 비교](project/2-2/db_agent_api.md)
- [여러 문자 전송 플랫폼 중, NCP를 선택한 이유](project/2-2/ncp.md)
- [OpenFeign과 Reactive Feign 비교. 비동기 전송이 목적일 때, WebClient를 제외한 이유는?](project/2-2/reactive_feign.md)
- [문자 전송 성능이 200ms → 9ms로 개선된 과정은 어떻게 이루어졌나요?](project/2-2/reactive_feign_perform.md)

### 2-3. 송아리에어 서브사용자 모니터링 기능 개발

- [SSE, WebSocket, MQTT의 동작 방식을 설명해주세요.](project/2-3/sse_websocket_mqtt.md)
- [실시간 알림임에도 REST 방식을 선택한 이유는 무엇인가요?](project/2-3/realtime_rest.md)

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

### 2-8. 이미지 리사이징 처리 서버 구축

- [이미지 처리 서버 구축시, Thumbor를 택한 이유](project/2-8/why_thumbor.md)

### 2-9. 송아리당뇨 API Server 마이그레이션

- [모놀리식 아키텍처 구조의 프로젝트를 마이크로서비스로 전환한 이유](project/2-9/why_msa.md)
- [대용량 데이터(약 60만 건) 조회 성능을 개선한 방법은 무엇인가요?](cs/database/db_60_perform.md)

<br/>

## 인성 면접

업로드 예정