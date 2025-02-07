## N+1 문제와 해결책

<br/>

> N+1 문제란?
>
- **N+1 문제**는 **JPA에서 연관된 엔티티를 조회할 때 발생할 수 있는 성능 문제로, 다대일(N:1) 또는 일대다(1:N) 관계**에서 **지연 로딩(Lazy Loading)** 전략을 사용할 경우 자주 발생합니다.

<br/>

> **N+1 문제 예시**
>
- 예를 들어, `User`와 `Order` 엔티티가 일대다(OneToMany) 관계를 맺고 있다고 가정해 봅시다.
- `User` 객체를 조회하면서 각 사용자가 가진 **`Order`** 목록을 조회할 때, **`Lazy Loading`*을 사용하면 다음과 같은 일이 발생합니다:
  1. `User` 엔티티를 조회하는 첫 번째 쿼리 (1번 쿼리)
  2. 각 `User`가 가진 `Order` 목록을 조회하는 **N개의 추가 쿼리** (N번 쿼리)

<br/>

> N+1 문제 해결 방법
>
1. **`@Query`나 `JPQL`을 활용한 조인 (JOIN FETCH)**
    - 패치조인(`JOIN FETCH`)을 사용하여 **연관된 엔티티를 한 번의 쿼리 함께 조회합니다.**

1.  **`EntityGraph` 사용**
    - `EntityGraph`*를 사용하면 **명시적으로 연관된 엔티티를 함께 조회**하도록 지정 가능
    - `JOIN FETCH`와 유사하지만, **쿼리에서 동적으로 연관 엔티티를 선택하여 성능을 최적화** 가능

    ```java
    @EntityGraph(attributePaths = {"orders"})
    User findUserWithOrders(Long userId);
    ```