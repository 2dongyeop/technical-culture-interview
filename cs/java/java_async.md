## 비동기 처리 및 스레드 관리

> `ExecutorService`와 `ForkJoinPool`
>

- **`ExecutorService`:**
    - **스레드 풀**을 관리하여 효율적으로 비동기 작업을 처리.
    - `FixedThreadPool`, `CachedThreadPool` 등 다양한 구현체 존재.
    - **CPU 바운드 작업보다 I/O 바운드 작업에 최적화**됨.
- **`ForkJoinPool`:**
    - **작업을 분할(Fork)**하고 **병렬로 처리(Join)**하는 방식.
    - 주로 **재귀적인 작업 분할**이 필요한 경우에 사용.
    - Java 8부터 `parallelStream()`, `CompletableFuture` 기본 스레드 풀로 활용됨.

<br/>

> `CompletableFuture`의 주요 기능과 활용 방법은?
>

- `CompletableFuture`란?
    - Java 8에서 도입된 **비동기 프로그래밍 API**.
    - 콜백 지옥을 방지하고, 명령형 코드 스타일로 비동기 로직 작성 가능.
- 주요 메서드:
    - `supplyAsync()`: 비동기 작업 실행.
    - `thenApply()`: 이전 결과를 받아서 처리.
    - `thenCombine()`: 두 개의 비동기 결과를 결합.
    - `exceptionally()`: 예외 처리

<br/>

- https://github.com/kwon37xi/java-spring-thread-pool-test