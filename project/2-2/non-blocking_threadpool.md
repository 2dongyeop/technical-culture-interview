## 논블로킹 형태의 클라이언트를 사용해서 성능을 개선하신 것 같은데.. 그럼 만약에 스레드풀을 충분히 많은 양으로 설정해놓았다면, 지금 개선하신 방식과 어떤 차이가 있을까요? 스레드풀의 크기가 클 경우에 발생하는 문제점은 무엇일까요?

<br/>

> 면접관님 생각
>
> 아마. 서버의 메모리등과 같은 리소스만 충분하다면, 스레드 풀을 늘려도 문제는 안될 것 같아요.
> 다만, 물론 스레드를 사용하는 것 자체도 자바에서도 Thread 객체를 생성해서 사용하다보니, 자연스레 메모리가 할당될거고.. 이런 것들이 자원의 소모로 이어질 것 같네요 ㅎㅎ

<br/>

> 스레드풀 개수가 작을 때의 문제점

- 처리량(Throughput) 저하
    - → 동시 처리할 수 있는 작업 개수가 적어, 처리 속도가 느려지고 대기 시간이 증가함.
- 큐 대기 증가
    - → 요청이 많으면 작업 큐에 대기하는 작업이 쌓여 응답 지연(latency)이 발생.
- 타임아웃 발생 가능성
    - → 클라이언트의 요청이 오래 대기하면 타임아웃으로 인해 실패할 가능성이 높아짐.
- CPU 활용도 저하
    - → CPU 코어 개수보다 스레드 개수가 너무 적으면 자원을 충분히 활용하지 못해 성능이 낮아짐.

<br/>

> 스레드풀 개수가 클 때의 문제점

- 컨텍스트 스위칭 비용 증가
    - → 너무 많은 스레드가 실행되면 CPU가 컨텍스트 스위칭에 많은 시간을 소비해 성능 저하 발생.
- 메모리 부족(OOM) 가능성
    - → 각 스레드는 스택 메모리를 할당받는데, 너무 많은 스레드가 생성되면 OutOfMemoryError 발생 가능.
- 스케줄링 오버헤드 증가
    - → 운영체제가 많은 스레드를 관리해야 하므로, 스레드 스케줄링 오버헤드가 커져 성능이 저하됨.
- 락(Contention) 문제 심화
    - → 공유 자원을 다수의 스레드가 동시에 접근하면 락 경쟁이 발생해 성능이 떨어질 수 있음.
