## Transaction이란 무엇인가? @Transaction 애너테이션의 주요 옵션에 대해 설명

<br/>

> 트랜잭션 개념
>
- **데이터베이스에서 하나의 논리적인 작업 단위를 구성하는 연산들의 집합**
- **모든 작업이 성공해야만 변경사항을 반영(Commit)하고, 하나라도 실패하면 원래 상태로 복구(Rollback)하는 원자적(Atomic) 연산**

<br/>

> 트랜잭션 ACID 원칙
>
- **Atomicity (원자성) :** 트랜잭션의 작업이 **모두 반영되거나, 전혀 반영되지 않음** (Rollback 지원)
- **Consistency (일관성) :** 트랜잭션이 성공하면, 데이터베이스는 **일관된 상태 유지**
- **Isolation (격리성) :** 여러 트랜잭션이 동시에 실행되더라도 **서로 간섭하지 않음**
- **Durability (지속성) :** 트랜잭션이 성공적으로 완료되면, **결과가 영구적으로 저장됨**

<br/>

> `@Transaction` 애너테이션의 주요 옵션에 대해 설명
>
1. `propagation` (트랜잭션 전파 옵션)

    | 전파 옵션 | 설명 |
    | --- | --- |
    | **REQUIRED** (기본값) | 기존 트랜잭션이 있으면 참여하고, 없으면 새로 생성 |
    | **REQUIRES_NEW** | 기존 트랜잭션이 있어도 무조건 새로운 트랜잭션을 생성 |
    | **NESTED** | 부모 트랜잭션 내에서 중첩된 트랜잭션 생성 (부분 롤백 가능) |
    | **MANDATORY** | 기존 트랜잭션이 없으면 예외 발생 |
    | **SUPPORTS** | 트랜잭션이 있으면 참여하고, 없으면 트랜잭션 없이 실행 |
    | **NOT_SUPPORTED** | 트랜잭션 없이 실행 |
    | **NEVER** | 트랜잭션이 있으면 예외 발생 |
2. `isolation` (트랜잭션 격리 수준)
    - **READ UNCOMMITTED :** 커밋되지 않은 데이터 읽기 가능
    - **READ COMMITTED : 커밋된 데이터만 읽기 가능**
    - **REPEATABLE READ : 트랜잭션 내에서 동일한 데이터를 읽음**
    - **SERIALIZABLE : 가장 강력한 격리 수준, 동시 실행 불가**
3. `readOnly` (읽기 전용 모드)
    - 트랜잭션이 **데이터 조회만 수행할 때 최적화**를 위해 사용
    - 데이터 변경을 시도하면 예외 발생 가능 (DB에 따라 다름)
    - 내부적으로 Hibernate는 **Flush 모드를 끄고 성능 최적화**
4. `rollbackFor` (강제 롤백할 예외 지정)
    - 기본적으로 Spring의 `@Transactional`은 **`RuntimeException`과 `Error`가 발생할 때만 자동 롤백**
    - `Checked Exception`(`SQLException`, `IOException` 등)은 자동 롤백되지 않음
    - `rollbackFor`을 사용하면 **Checked Exception도 롤백 가능**