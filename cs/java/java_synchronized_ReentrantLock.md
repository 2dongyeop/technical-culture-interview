## synchronized 과 ReentrantLock

모두 **스레드 동기화**를 위한 메커니즘

<br/>

1. `synchronized`

- **내부적으로 락을 관리:**
    - `synchronized` 블록 또는 메서드에 대한 진입과 종료 시 자동으로 락을 획득하고 해제
- **자동 해제:**
    - 스레드가 `synchronized` 블록을 벗어나면 자동으로 락이 해제됩니다.
- **조건적 대기, 알림 기능 없음:**
    - `synchronized` 자체는 스레드의 대기 및 알림 기능을 제공하지 않지만,
      `Object.wait()`, `Object.notify()` 메서드를 사용하여 수동으로 대기와 알림을 처리 가능

<br/>

2. `ReentrantLock`

- `Lock` 인터페이스의 구현체로 **명시적으로 락을 제어**
    - `lock()`으로 락을 획득하고 `unlock()`으로 락을 해제
- **재진입성**:
    - `ReentrantLock`은 스레드가 이미 보유한 락을 다시 획득할 수 있도록 합니다(재진입성).
    - 즉, **같은 스레드가 여러 번 락을 획득해도 교착 상태가 발생하지 않습니다.**
- **조건적 대기와 알림 기능**:
    - `ReentrantLock`은 `Condition` 객체를 사용하여 스레드 간 대기 및 알림 기능을 제공
- **비차단 대기:**
    - `ReentrantLock`은 `tryLock()` 메서드를 통해 **락을 획득할 수 없을 때 기다리지 않고 즉시 반환**