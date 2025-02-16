# technical-interview

이직을 준비하면서 필요한 내용들을 정리한 자료입니다.
모두 행복하세요.

### 목차

1. [기술면접 : CS 지식부터 개인 프로젝트 기반 기술 면접까지](#기술-면접)
2. [인성/컬쳐핏 면접 : 메타인지부터 조직문화 적합성까지](#인성-및-컬쳐핏-면접)
3. [면접관 역질문](#면접관-역질문-리스트)
4. [기타](#기타)
    - [이력서 작성 시 참고하면 좋을 자료들](#이력서-작성-시-참고하면-좋을-자료들)
    - [CS 지식 정리 시 참고하면 좋을 자료들](#cs-지식-정리-시-참고하면-좋을-자료들)
    - [이직 준비시 멘탈 관리](#이직-준비시-멘탈-관리)

<br/>

# 기술 면접

## 1. CS

### 1-1. Java

- [자료구조 및 Java 컬렉션. with 동적 크기 조정](cs/java/java_%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0_%EC%BB%AC%EB%A0%89%EC%85%98.md)
- [추상클래스와 인터페이스의 차이](cs/java/java_%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4.md)
- [volatile 키워드는 무엇이고 언제 사용하나요?](cs/java/java_volatile.md)
- [synchronized 와 ReentrantLock](cs/java/java_synchronized_ReentrantLock.md)
- [ThreadLocal](cs/java/java_threadlocal.md)
- [GC 별 특징 및 구조, 동작 과정](cs/java/java_gc.md)
- [비동기 처리 및 스레드 관리](cs/java/java_async.md)
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
- [**Spring Cloud MSA 관련 모든것**](https://github.com/2dongyeop/spring-cloud-msa)

### 1-3. JPA

- [JPA는 무엇이며 어떤 특징/장점이 있는가?](cs/spring/spring_what_is_jpa.md)
- [Transaction이란 무엇인가? @Transaction 애너테이션의 주요 옵션에 대해 설명](cs/spring/spring_transaction.md)
- [영속성 컨텍스트란 무엇인가?](cs/spring/spring_context.md)
- [N+1 문제와 해결책](cs/spring/spring_jpa_n1.md)
- [JPA OSIV(Open Session In View) 설정](cs/spring/spring_jpa_osiv.md)

### 1-4. Database

- [SQL vs NoSQL , 하이브리드 아키텍처 설계](cs/database/db_sql_nosql.md)
- [정규화/반정규화](cs/database/db_normalization.md)
- [인덱스란?](cs/database/db_index.md)
- [인메모리 DB가 더 빠른 이유](cs/database/db_inmemory.md)
- [**인덱스가 있음에도 성능이 더 느린 경우가 있다. 이에 대해 설명해보시오.**](cs/database/db_index_invalid.md)
- [DB 인덱스가 어떤 자료구조로 이루어져 있어서, 성능을 향상시키나요?](cs/database/db_index_data_structure.md)
- [MySQL InnoDB의 기본 격리 수준이 어떻게 될까요?](cs/database/db_default_isolation_level.md)
- [MySQL MVCC 방식에 대해 설명해주세요.](cs/database/db_mysql_mvcc.md)
- [MySQL Gap Lock](cs/database/db_mysql_gaplock.md)
- [비관적 락과 낙관적 락에 대해 설명해주세요.](cs/database/db_lock.md)

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
> 내용은 [첨부한 이력서](https://github.com/2dongyeop/technical-interview/blob/main/resource/%EC%84%9C%EB%B2%84_%EA%B0%9C%EB%B0%9C%EC%9E%90_%EC%9D%B4%EB%8F%99%EC%97%BD_%EA%B2%BD%EB%A0%A5%EA%B8%B0%EC%88%A0%EC%84%9C.pdf)
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
- [**Retry 정책을 설계할 때 고려사항**](cs/spring/spring_retry.md)
- [테스트 코드 작성 원칙 및 전략이 있는지?](project/common/test_code.md)
- [여러 부하 테스트 툴(nGrinder, JMeter, k6, Locust) 중에서 nGrinder를 선택한 이유](project/common/load_test.md)
- [여러 APM 툴(Pinpoint, Datadog, Jaeger, New Relic, Zipkin) 중 Pinpoint을 선택한 이유](project/common/apm.md)

### 2-2. 문자 전송 클라이언트 변경

- [DB Agent 방식 vs API 방식 비교](project/2-2/db_agent_api.md)
- [여러 문자 전송 플랫폼 중, NCP를 선택한 이유](project/2-2/ncp.md)
- [OpenFeign과 Reactive Feign 비교. 비동기 전송이 목적일 때, WebClient를 제외한 이유는? 그리고 Reactive Feign의 단점.](project/2-2/reactive_feign.md)
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

> 답변 팁
>
> - 구체적인 경험을 포함하면 설득력이 높아집니다.
> - **STAR 기법**(상황, 과제, 행동, 결과)을 활용하면 논리적인 답변 구성이 가능합니다.
> - 면접을 보러 가는 회사 혹은 팀에서 운영하는 서비스에 대해서 알아가는 것도 중요합니다. 관심도가 영향을 미칠 수 있다고 생각해요.

### 지원 동기

- 짧은 자기소개
- 지원 동기
- 저희 회사에 대해 알고 계신 것이 있으실까요? (자사 서비스 이용)
- 현재 회사(혹은 이전 직장)를 떠나려는 이유는 무엇인가요?
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
- 같이 일하고 싶은 동료 유형과 같이 일하기 싫은 동료 유형
- 협업 중 의견 충돌이 발생했을 때 어떻게 해결하는 편인가요?
- 개발자로서 성장하기 위해 동료에게 기대하는 것이 있나요?

### 삶의 태도 및 가치관

- 장기적인 목표나 커리어 플랜이 있다면?
- 스트레스 해소 방법(취미, 주말)
- 삶에서 가장 중요하게 생각하는 가치
- 개발자로서 지속적으로 성장하기 위해 어떤 노력을 하고 있나요?

<br/>

# 면접관 역질문 리스트

### 업무 및 개발 프로세스 관련

- 신규 기능 개발 시, 업무프로세스가 어떻게 되나요?
- 배포 및 운영 프로세스는 어떻게 진행되나요?
- 장애 대응 및 온콜(야간 대응) 체계는 어떻게 되어 있나요?

### 팀 및 조직 문화 관련

- 팀 구성이 어떻게 되어 있나요?
- 팀에서 사용하는 기술 스택이 어떻게 되나요?
- 회사/팀 내 어떤 개발문화가 존재하나요?

### 커리어 성장 및 평가 관련

- 개발자의 성장을 위해 회사에서 제공하는 지원(스터디, 세미나, 컨퍼런스 참가 등)이 있나요?
- 신입/경력 개발자의 온보딩 프로세스는 어떻게 진행되나요?
- 입사를 하게 되면 담당하게 될 업무는 무엇인가요?
- 개인의 성장과 역량 개발을 위한 피드백/평가 방식이 있나요?
- 서비스에 대한 DAU/MAU 등의 사용 지표를 분석하고 있나요?

### 회사 및 비즈니스 관련

- 레퍼런스 체크는 어떤 방식으로 진행되나요?
- **지원한 회사에 스페시픽한 질문** 추가하기

<br/>

# 기타

### 이력서 작성 시 참고하면 좋을 자료들

커피챗을 통해 작성한 이력서를 피드백 받아보세요. 쑥스러워도 반드시 필요한 과정입니다. 본인의 이력서에 자신없다면, 면접관에게도 동일하게 보일 것이라고 생각해요.

- [진태양님](https://resume.dataportal.kr/)
- [요우님](https://resume.yowu.dev/)
- [Wonny | 데이터로 일하는 개발자 (Public)](https://www.notion.so/Wonny-Public-c2f8051bfb574f349406a30d2bc71a45?pvs=21)
- [이동욱님](https://jojoldu.github.io/)
- [아웃사이더님](https://blog.outsider.ne.kr/1234)

### 이직 준비시 멘탈 관리

- [바다쓰기님](https://xrabcde.github.io/moving-retrospection/)
- [최홍희님](https://vvshinevv.tistory.com/108)
- [카펀님](https://katfun.tistory.com/220)
- [이호승님](https://github.com/leehosung/awesome-devteam)

### CS 지식 정리 시 참고하면 좋을 자료들

- [정신차려 이 각박한 세상속에서](https://www.notion.so/f8114c9e2c774eccaca509f9618b7115?pvs=21)
- [NKLCWDT/CS](https://github.com/NKLCWDT/cs)
- [규글님](https://github.com/gyoogle/tech-interview-for-developer)
- [한재엽님](https://github.com/JaeYeopHan/Interview_Question_for_Beginner)
- [WeareSoft/tech-interview](https://github.com/WeareSoft/tech-interview)
- [cheese10yun님 TIL](https://github.com/cheese10yun/TIL)
- [남준이형 TIL](https://github.com/namjunemy/TIL)
- [2dongyeop님 TIL](https://github.com/2dongyeop/TIL)
- [VSfe님](https://github.com/VSFe/Tech-Interview?tab=readme-ov-file)
- [backtony/SW-Maestro-gjgs의 Tech 문서](https://github.com/backtony/SW-Maestro-gjgs/blob/master/TECH.md#-%EC%99%9C-%EC%9D%B4-%EA%B8%B0%EC%88%A0%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%96%88%EB%8A%94%EA%B0%80-)
- [신입 백엔드 면접 질문 Ver. 2.0.7](https://velog.io/@yukina1418/%EC%B5%9C%EA%B7%BC-%EB%A9%B4%EC%A0%91%EC%9D%84-%EB%8B%A4%EB%8B%88%EB%A9%B4%EC%84%9C-%EB%B0%9B%EC%95%98%EB%8D%98-%EC%A7%88%EB%AC%B8%EB%93%A4)

### 진짜 기타

- [이직, 퇴사 체크리스트](https://velog.io/@hyperperi/%EC%9D%B4%EC%A7%81%ED%87%B4%EC%82%AC-%EC%B2%B4%ED%81%AC%EB%A6%AC%EC%8A%A4%ED%8A%B8)


