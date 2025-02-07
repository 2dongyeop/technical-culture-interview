## JPA는 무엇이며 어떤 특징/장점이 있는가?

<br/>

> JPA란?
>
- JPA(Java Persistence API)는 **Java 애플리케이션에서 관계형 데이터베이스를 객체 지향적으로 다룰 수 있도록 하는 ORM(Object-Relational Mapping) 표준 인터페이스**
- 구현체로는 Hibernate가 가장 많이 사용됨.
- ORM : 객체(Entity)와 데이터베이스 테이블을 매핑하여 SQL을 직접 작성하지 않고도 데이터 조작 가능

<br/>

> 특징 및 장점
>
1. ORM (객체 지향적인 데이터베이스 접근)
    - **엔티티(Entity) 클래스와 테이블을 매핑하여 사용**
    - SQL 대신 **객체 조작만으로 데이터베이스 연동 가능**
2. 데이터베이스 독립성 (DBMS 종속성 제거)
    - JPA는 **DBMS에 의존하지 않는 표준 ORM**
    - MySQL, PostgreSQL, Oracle 등의 DB에 쉽게 변경 가능
3. **캐시 및 성능 최적화**
    - **1차 캐시**: 같은 트랜잭션 내에서 동일한 엔티티 조회 시, **DB 조회 없이 캐시에서 가져옴**
    - **쓰기 지연 (Write-Behind)**: `persist()` 시점이 아니라 **트랜잭션이 커밋될 때 쿼리를 실행**
    - **지연 로딩(Lazy Loading) 지원** → `@OneToMany(fetch = FetchType.LAZY)`
4. JPQL (객체지향 쿼리) 지원
    - SQL 대신 **JPQL(Java Persistence Query Language)을 사용하여 객체를 조회**
    - 데이터베이스 테이블이 아닌 **Entity를 대상으로 쿼리를 작성**
5. 자동 트랜잭션 관리 (Spring Data JPA)
    - JPA는 **트랜잭션을 자동으로 관리**하며, `@Transactional`을 사용하여 제어 가능