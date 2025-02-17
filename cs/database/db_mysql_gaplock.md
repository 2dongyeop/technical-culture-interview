## MySQL Gap Lock

> Dirty Read
>

1. 개념
    - 다른 트랜잭션에서 아직 커밋되지 않은 데이터를 읽는 현상
2. 발생하는 격리 수준:
    - READ UNCOMMITTED
3. 문제점:
    - 트랜잭션 A가 아직 **커밋하지 않은 변경 사항**을 트랜잭션 B가 읽음
    - 이후 트랜잭션 A가 롤백하면, 트랜잭션 B는 **존재하지 않는 데이터를 읽은 것**이 됨
4. 해결 방법
    - READ COMMITTED 이상으로 격리 수준을 설정하면 Dirty Read 방지 가능

<br/>

> Non-Repeatable Read
>

1. 정의
    - 같은 트랜잭션 내에서 동일한 SELECT 쿼리를 실행했을 때, 서로 다른 결과가 나오는 현상
2. 발생하는 격리 수준:
    - READ COMMITTED
3. 문제점:
    - 트랜잭션 A가 데이터를 읽는 동안, 다른 트랜잭션에서 해당 데이터를 변경 및 커밋하면 값이 달라짐
    - 동일한 SELECT 쿼리를 실행해도 결과가 달라짐 → 일관성이 깨짐
4. 해결 방법:
    - REPEATABLE READ 이상으로 격리 수준을 설정하면 Non-Repeatable Read 방지 가능
    - REPEATABLE READ에서는 트랜잭션이 시작되면 동일한 데이터를 읽을 수 있도록 MVCC로 관리

<br/>

> Phantom Read
>

1. 정의:
    - 같은 트랜잭션 내에서 동일한 조건으로 조회했을 때, 새로운 행이 추가되거나 삭제되어 결과가 달라지는 현상
2. 발생하는 격리 수준:
    - REPEATABLE READ (InnoDB에서는 Gap Lock으로 방지)
3. 문제점:
    - 트랜잭션 A가 특정 조건으로 데이터를 조회한 후, 같은 조건으로 다시 조회했을 때 **새로운 행이 추가되거나 삭제됨**
    - **같은 SELECT 쿼리를 실행해도 결과 집합이 다름**

<br/>

> Gap Lock
>

1. 개념
    - Gap Lock은 InnoDB에서 REPEATABLE READ 격리 수준을 유지하면서도 Phantom Read를 방지하기 위해 사용하는 잠금 기법입니다.
    - 기본적으로 레코드 자체뿐만 아니라, 레코드 사이의 "갭(틈)"까지 잠그는 방식입니다.

1. Gap Lock이 필요한 이유 : Phantom Read 방지
    - 일반적인 레코드 잠금(Row Lock)만 사용하면 새로운 데이터 삽입(INSERT)을 막을 수 없음
    - 예를 들어, 트랜잭션 A가 특정 범위의 데이터를 조회하고 있는 동안, 트랜잭션 B가 새로운 데이터를 삽입하면 같은 조회를 다시 실행할 때 결과가 달라질 수 있음
    - 이를 방지하기 위해 InnoDB는 Gap Lock을 사용하여 특정 범위 내에서 INSERT를 차단

1. Gap Lock으로 인한 문제점
    1. INSERT 블로킹 현상

        ```sql
        SELECT * FROM orders WHERE price BETWEEN 100 AND 200 FOR UPDATE;
        ```

        - 트랜잭션이 끝나기 전까지 다른 트랜잭션에서 `price`가 100~200 사이인 데이터를 삽입할 수 없음
        - 삽입 성능이 저하될 수 있음
        - 해결 방법: 트랜잭션을 짧게 유지하거나, 필요한 경우 READ COMMITTED로 격리 수준 변경
    2. 데드락(Deadlock) 가능성 증가
        - 두 개의 트랜잭션이 서로 다른 범위의 데이터에 대해 Gap Lock을 걸고, 상대방이 잠근 데이터를 필요로 하는 경우 데드락이 발생할 수 있음
        - 해결 방법: 트랜잭션 수행 순서를 일관되게 유지하거나, 필요 없는 경우 READ COMMITTED로 낮춤