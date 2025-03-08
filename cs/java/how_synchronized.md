## Synchronized는 어떤 내부 원리로 락을 동작시키는지 설명해주세요.(뮤텍스락)

### synchronized의 내부 원리

- synchronized는 JVM 수준에서 락을 관리하는 동기화 메커니즘
- 객체(Object) 또는 클래스(Class) 단위로 모니터 락(Monitor Lock)을 획득하여 동기화
- 내부적으로 JVM의 모니터(monitor)와 운영체제의 Mutex(뮤텍스) 락을 활용

<br/>

### JVM에서 synchronized가 동작하는 원리

synchronized 키워드를 만나면, JVM이 객체의 모니터(Monitor)를 이용하여 락을 관리합니다.

> 모니터(Monitor)란?

- JVM 내부의 객체마다 존재하는 락(lock)
- 특정 스레드가 객체의 모니터를 획득하면, 다른 스레드는 대기해야 함.
