## DB 혹은 쿼리 성능최적화 경험이 있는지?

<br/>

> **경험한 DB 성능 최적화 사례**
>

1. **복합 인덱스를 활용한 쿼리 최적화 (MySQL)**
    - **상황:**
        - `order_history` 테이블에서 **특정 유저의 최근 3개월 주문 내역을 조회**하는 쿼리
        - `WHERE user_id = ? AND order_date >= ?` 조건을 사용
        - 실행 시간이 **1.5초 → 100ms**로 단축
    - **최적화 방법:**
        1. 기존 인덱스: `INDEX(user_id)` → **사용은 되지만, 범위 조건(order_date)에서 비효율적**
        2. **복합 인덱스 적용**: `INDEX(user_id, order_date)` 추가
        3. 실행 계획 (`EXPLAIN`) 확인 후 **Using index** 활용되는지 체크

1. **Slow Query Log 및 실행 계획 (EXPLAIN ANALYZE) 활용**
    - 실행 계획을 통해 **Index 사용 여부, Full Table Scan 발생 여부** 체크
    - **MySQL**: `SHOW PROCESSLIST;`, `EXPLAIN`, `ANALYZE`

        ```sql
        # MySQL 8.0 (EXPLAIN, EXPLAIN ANALYZE 모두 사용 가능)
        EXPLAIN ANALYZE SELECT * FROM orders WHERE user_id = 123;
        
        # MySQL 5.7 (EXPLAIN만 사용 가능)
        EXPLAIN SELECT * FROM orders WHERE user_id = 123;
        ```
3. 인덱스가 존재하지만, 성능이 개선되지 않는 사례를 조사
    - [관련 링크](database/db_inmemory.md)

<br/>

> **DB 성능 최적화를 위한 전략**
>

1. **데이터 정규화 vs 비정규화 균형 조절**
    - 조회가 잦은 경우 **중복 데이터를 허용하는 비정규화도 고려**
    - 너무 많은 JOIN 발생 시 **중간 테이블 (Aggregation Table) 생성**
2. **캐싱 활용**
    - **Redis, Memcached** 등을 사용하여 **자주 조회되는 데이터 캐싱**
    - MySQL Query Cache 대신 **애플리케이션 단에서 캐싱**