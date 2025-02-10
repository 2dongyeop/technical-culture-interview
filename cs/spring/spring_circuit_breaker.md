## Circuit Breaker 패턴이 필요한 이유 & Spring Cloud Resilience4j 주요 기능

> **Circuit Breaker 패턴이 필요한 이유**
>

1. **장애 확산 방지**
    - 외부 API나 서비스 장애 발생 시, **무한 대기 방지 & 빠른 오류 반환**
    - 장애가 전파되지 않도록 호출을 차단하여 서비스 안정성 유지
2. **서비스 복구 시간 단축**
    - 장애 발생 시 일정 시간 동안 요청을 차단 (OPEN 상태)
    - 이후 **점진적 복구 (HALF-OPEN → CLOSED)** 를 통해 정상 상태 복귀
3. **불필요한 리소스 낭비 방지**
    - 실패한 요청을 계속 시도하면 시스템 부하 발생
    - Circuit Breaker를 통해 불필요한 재시도를 방지

<br/>

> **Spring Cloud Resilience4j 주요 기능**
>

1. **Circuit Breaker** (서킷 브레이커)
    - 장애 발생 시 **OPEN** 상태로 전환하여 요청 차단
    - 일정 시간 후 **HALF-OPEN** 상태로 일부 요청 허용
    - 성공률이 정상화되면 **CLOSED** 상태로 복귀

1. **Rate Limiter** (속도 제한)
    - 초당 호출 횟수를 제한하여 과부하 방지
    - 예: **최대 10 TPS 제한 설정**

1. **Retry** (재시도)
    - 일시적 오류 발생 시 일정 횟수까지 재시도