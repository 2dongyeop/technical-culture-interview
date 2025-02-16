## MySQL Gap Lock

Gap Lock은 InnoDB에서 REPEATABLE READ 격리 수준을 유지하면서도 Phantom Read를 방지하기 위해 사용하는 잠금 기법입니다.

기본적으로 레코드 자체뿐만 아니라, 레코드 사이의 "갭(틈)"까지 잠그는 방식입니다.

<br/>

> Gap Lock이 필요한 이유 : Phantom Read 방지
>

- 일반적인 레코드 잠금(Row Lock)만 사용하면 새로운 데이터 삽입(INSERT)을 막을 수 없음
- 예를 들어, 트랜잭션 A가 특정 범위의 데이터를 조회하고 있는 동안, 트랜잭션 B가 새로운 데이터를 삽입하면 같은 조회를 다시 실행할 때 결과가 달라질 수 있음
- 이를 방지하기 위해 InnoDB는 Gap Lock을 사용하여 특정 범위 내에서 INSERT를 차단

<br/>

> Gap Lock으로 인한 문제점
>

1. INSERT 블로킹 현상

    ```sql
    SELECT * FROM orders WHERE price BETWEEN 100 AND 200 FOR UPDATE;
    ```

    - 트랜잭션이 끝나기 전까지 다른 트랜잭션에서 `price`가 100~200 사이인 데이터를 삽입할 수 없음
    - 삽입 성능이 저하될 수 있음
    - 해결 방법: 트랜잭션을 짧게 유지하거나, 필요한 경우 READ COMMITTED로 격리 수준 변경

1. 데드락(Deadlock) 가능성 증가
    - 두 개의 트랜잭션이 서로 다른 범위의 데이터에 대해 Gap Lock을 걸고, 상대방이 잠근 데이터를 필요로 하는 경우 데드락이 발생할 수 있음
    - 해결 방법: 트랜잭션 수행 순서를 일관되게 유지하거나, 필요 없는 경우 READ COMMITTED로 낮춤