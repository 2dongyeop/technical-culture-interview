## 비관적 락과 낙관적 락에 대해 설명해주세요.

추가 자료 : https://github.com/2dongyeop/concurrency-solution?tab=readme-ov-file#2-db-lock

비관적 락(Pessimistic Lock)과 낙관적 락(Optimistic Lock)은 **동시성 제어를 위한 두 가지 주요 방식**입니다.

<br/>

> **비관적 락 (Pessimistic Lock)**
>

- **데이터 충돌 가능성이 높을 때 사용**
- 트랜잭션이 데이터를 읽거나 수정할 때, **먼저 락을 걸어 다른 트랜잭션이 접근하지 못하도록 차단**
- MySQL에서는 **SELECT ... FOR UPDATE (Exclusive Lock)**, **LOCK IN SHARE MODE (Shared Lock)**을 사용
- 장점: 충돌이 발생하지 않아 데이터 정합성이 보장됨
- 단점: 락이 걸린 동안 다른 트랜잭션이 기다려야 해서 성능 저하 가능

<br/>

> **낙관적 락 (Optimistic Lock)**
>

- **데이터 충돌 가능성이 낮을 때 사용**
- 데이터 수정 시점에만 충돌을 검사하며, **버전 번호(versioning)나 타임스탬프(timestamp) 비교 방식** 사용
- 보통 **`UPDATE ... WHERE version = ?` 같은 방식으로 적용**
- 실패 시 재시도 로직 필요
- 장점: 락을 걸지 않아 동시 처리량이 높음
- 단점: 충돌 발생 시 재시도가 필요하고, 충돌이 많으면 성능 저하 가능