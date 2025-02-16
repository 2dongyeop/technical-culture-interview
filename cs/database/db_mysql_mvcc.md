## MySQL MVCC 방식에 대해 설명해주세요.

MVCC (Multi-Version Concurrency Control)는 **트랜잭션이 서로 충돌하지 않도록 여러 버전의 데이터를 관리하여 동시성을 향상**시키는 기법입니다.

**MySQL InnoDB에서 MVCC가 동작하는 방식:**

- `trx_id` (트랜잭션 ID)와 `undo log`를 활용하여 **각 트랜잭션이 볼 수 있는 데이터 버전을 결정**합니다.
- **SELECT 실행 시**:
    - `READ COMMITTED`에서는 **가장 최근에 커밋된 데이터**를 읽음.
    - `REPEATABLE READ`에서는 **트랜잭션 시작 시점의 스냅샷을 유지**하여 같은 데이터를 읽음.
- **DELETE / UPDATE 실행 시**:
    - 기존 데이터를 바로 삭제하지 않고, 새로운 버전의 데이터를 생성하며 이전 버전은 `undo log`로 보관.
- **INSERT 시**:
    - 트랜잭션 ID를 부여하고 새로운 레코드를 추가.

이러한 방식으로 **락을 최소화하면서도 일관성을 유지**할 수 있습니다.