## `@Async` 애너테이션이 완벽한 비동기가 아닌 이유에 대해 자세히 설명해주세요.

<br/>

> 비동기 방식 차이 설명

- @Async는 Spring의 TaskExecutor(기본적으로 ThreadPoolTaskExecutor)를 사용하여 백그라운드 스레드 풀에서 실행됩니다.
    - 따라서, 결국 스레드 풀 개수만큼 동시 처리가 제한됩니다.
    - 즉, 스레드가 부족하면 대기(Blocking) 상태가 발생하고, 문맥 교환(Context Switching) 오버헤드도 존재합니다.

<br/>

- 반면, Reactive Feign(WebClient 기반)는 Netty를 활용한 이벤트 루프(Event Loop) 모델로 동작합니다.
    - 따라서 소수의 스레드(일반적으로 CPU 코어 수)만으로도 수많은 요청을 논블로킹 방식으로
      처리할 수 있습니다.
    - 결국, 대량의 동시 요청이 있을 때 스레드 풀이 아닌 이벤트 기반으로 더 많은 요청을 처리할 수 있어 성능이 향상됩니다.

<br/>

- 즉, @Async는 스레드 풀에서 스레드를 차지하고, Reactive Feign(WebClient)은 스레드 자원을 최소화하여 논블로킹 방식으로 처리하기 때문에 차이가 발생합니다.

<br/>
