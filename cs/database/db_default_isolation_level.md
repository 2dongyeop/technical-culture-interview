## MySQL InnoDB의 기본 격리 수준이 어떻게 될까요?

MySQL InnoDB의 기본 트랜잭션 격리 수준은 **REPEATABLE READ**입니다.

격리 수준을 정리하면 다음과 같습니다:

- **READ UNCOMMITTED**: 다른 트랜잭션의 커밋되지 않은 변경 사항까지 읽을 수 있음 → Dirty Read 발생 가능
- **READ COMMITTED**: 다른 트랜잭션이 커밋한 데이터만 읽을 수 있음 → Non-Repeatable Read 발생 가능
- **REPEATABLE READ (기본값)**: 트랜잭션이 시작되면 같은 쿼리 결과는 항상 동일 → Phantom Read 발생 가능 (InnoDB에서는 **Gap Lock으로 방지**)
- **SERIALIZABLE**: 모든 트랜잭션이 순차적으로 실행되는 것처럼 동작 → 성능 저하 가능

InnoDB는 **REPEATABLE READ를 사용하면서, MVCC와 Gap Lock을 활용하여 Phantom Read 문제까지 해결**합니다.