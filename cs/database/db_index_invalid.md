## 인덱스가 있음에도 성능이 더 느린 경우가 있다. 이에 대해 설명해보시오.

<br/>

인덱스는 잘못 사용하면 오히려 성능을 저하시킬 수 있습니다.

항상 **실제 실행 계획(`EXPLAIN ANALYZE`)을 확인하고, 적절한 인덱스 전략을 설계하는 것이 중요**

<br/>

> **인덱스가 과도하게 많을 때 (Index Overhead)**
>

- **문제:**
    - 테이블에 **불필요하게 많은 인덱스**가 존재하면, `INSERT`, `UPDATE`, `DELETE` 성능이 저하됨.
    - **데이터 변경 시 모든 관련 인덱스를 갱신해야 하므로 추가적인 디스크 I/O 발생**.
    - 특히 트랜잭션이 많은 OLTP 환경에서는 과도한 인덱스가 성능을 저하시킬 수 있음.
- **해결 방법:**
    - 사용하지 않는 인덱스를 주기적으로 점검 (`SHOW INDEX FROM table_name;`)
    - `EXPLAIN ANALYZE` 결과를 보고 **실제 사용되는 인덱스만 유지**

<br/>

> **잘못된 인덱스 선택 (Index Misuse)**
>

- **문제:**
    - 복합 인덱스(`(A, B, C)`)가 있는데 **WHERE 절이 첫 번째 컬럼(A) 없이 B, C만 검색하면 인덱스가 제대로 활용되지 않음**.
    - MySQL, PostgreSQL에서는 **복합 인덱스의 "선두 컬럼"이 WHERE 조건에 포함되지 않으면 인덱스를 사용할 수 없음**.
- **해결 방법:**
    - 인덱스 컬럼 순서를 `WHERE`, `ORDER BY`, `GROUP BY` 절의 사용 패턴에 맞게 설계
    - 위 예시에서는 `(B, A, C)` 순서로 인덱스를 재설계하거나, 단일 인덱스를 추가하는 것이 해결책이 될 수 있음

<br/>

> **낮은 선택도 (Low Selectivity)**
>

- **문제:**
    - **선택도(Selectivity) = 특정 값의 고유한 비율**이 낮으면 인덱스를 사용해도 효과가 없음.
    - 예를 들어, `gender = 'M'` 같은 조건은 전체 행 중 50%를 차지할 수 있음 → **풀 테이블 스캔이 더 효율적**
    - 인덱스는 **중복이 적고 고유한 값이 많은 경우** 효과적임.
- **해결 방법:**
    - 선택도가 낮은 컬럼(예: `성별`, `상태 값`)에 **단일 인덱스를 피하고, 복합 인덱스를 활용**
    - 예를 들어, `(gender, age, region)`처럼 추가적인 필드를 포함하면 선택도를 높일 수 있음

<br/>

> **인덱스 범위 스캔 (Index Range Scan)**
>

- **문제:**
    - `LIKE '%keyword'`처럼 앞부분이 `WILDCARD`로 시작하면 **B-Tree 인덱스를 사용할 수 없음**.

        ```sql
        SELECT * FROM products WHERE name LIKE '%Phone'; -- ❌ 인덱스 사용 안 함
        ```

    - 범위 조회 (`>`, `<`, `BETWEEN`)에서도 인덱스가 일부만 사용되거나 효율이 떨어질 수 있음.
- **해결 방법:**
    - `LIKE` 검색 최적화를 위해 **Full-Text Index (MySQL) 또는 ElasticSearch 사용**
    - `BETWEEN` 대신 **별도의 파티셔닝(partitioning) 적용**

<br/>

> **너무 큰 인덱스 (Large Index Size)**
>

- **문제:**
    - 인덱스가 너무 크면, **디스크에서 불필요한 페이지를 읽는 비용이 증가**
    - 특히 **VARCHAR(255) 같은 긴 문자열에 대한 인덱스는 비효율적**
- **해결 방법:**
    - 긴 문자열 컬럼은 **프리픽스 인덱스** 사용 (`VARCHAR(255)` 대신 `VARCHAR(50)` 인덱스 적용)

        ```sql
        CREATE INDEX idx_name ON users(name(50)); -- 앞 50자만 인덱스 사용
        ```

    - 필요하면 **커버링 인덱스 (Covering Index)** 활용

<br/>

> **ORDER BY와 인덱스 불일치**
>

- **문제:**
    - `ORDER BY` 절에서 **인덱스 정렬 순서와 다르면 정렬 비용(Sorting Cost)이 증가**

        ```sql
        -- (A, B) 복합 인덱스가 있는 경우
        SELECT * FROM users ORDER BY B; -- ❌ 인덱스 정렬과 다름
        ```

    - 인덱스를 사용해도 **추가적인 정렬 연산(Sorting Operation)이 필요**
- **해결 방법:**
    - `ORDER BY`와 **인덱스 정렬 순서를 맞추거나, "파일 정렬(FileSort)"을 피할 수 있도록 적절한 인덱스 추가**