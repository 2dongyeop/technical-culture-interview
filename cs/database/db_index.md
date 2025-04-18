## 인덱스란?

> 인덱스 정의
>

- DB에서 **검색 성능을 향상**시키기 위해 특정 컬럼에 대해 **데이터의 위치 정보를 저장하는 자료구조**
- 인덱스를 사용하면 데이터베이스가 전체 테이블을 **Full Scan**하는 대신, 인덱스를 통해 원하는 데이터를 빠르게 찾을 수 있습니다.

<br/>

> 인덱스 장점
>

- **검색 성능 향상**: 테이블 전체를 검색하는 **Full Table Scan**을 줄이고, **Index Scan**을 사용하여 속도를 개선함.
- **ORDER BY 최적화**: 정렬이 필요한 경우, 인덱스를 활용하여 정렬 비용을 감소시킬 수 있음.
- **JOIN 성능 개선**: 조인 연산 시, 인덱스를 활용하면 빠르게 조인 가능.

<br/>

> 인덱스 단점
>

- **INSERT/UPDATE/DELETE 성능 저하**: 인덱스를 유지하기 위해 추가적인 연산이 필요하여 DML 성능이 떨어질 수 있음.
- **디스크 공간 추가 사용**: 인덱스도 별도의 저장 공간을 차지하므로 대규모 테이블에서는 관리 부담이 증가함.
- **과도한 인덱스는 오히려 성능 저하**: 너무 많은 인덱스를 생성하면, 오버헤드가 커져 최적화가 필요함.

<br/>

> 인덱스를 활용한 성능 최적화
>

1. **적절한 컬럼에 인덱스 적용**
    - **자주 WHERE 조건으로 사용되는 컬럼** → 인덱스 추가
    - **ORDER BY, GROUP BY 에 자주 사용되는 컬럼** → 정렬 비용 절감
2. **복합 인덱스 활용**
    - **(A, B) 복합 인덱스**는 `WHERE A = ? AND B = ?` 시에만 효율적
    - `WHERE B = ?` 만 사용할 경우, 인덱스가 활용되지 않을 수도 있음 → 컬럼 순서 고려 필요