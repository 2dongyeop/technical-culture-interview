## ConcurrentHashMap은 내부적으로 어떻게 동시성 이슈를 해결했는지 아시나요? (CAS)

### 구조

- 내부적으로 배열 + 연결 리스트(또는 트리) 구조를 가짐.
- 각 버킷(배열의 인덱스) 단위로 동시성을 제어함.

<br/>

### 동시성 제어 방식

> 읽기(Reading):

- 대부분 락 없이 수행 (volatile 사용 => 값을 캐시가 아닌 메모리에서 직접 로드).
- get() 메서드는 기본적으로 락 없이 동작.

> 쓰기(Writing):

- CAS(Compare-And-Swap) 연산을 사용하여 동시성을 보장.
- 만약 CAS 실패 시, synchronized 블록으로 후처리.
- 테이블 크기가 일정 수준을 넘어서면 트리(TreeBin)로 변환하여 성능 개선.

<br/>

### CAS(Compare And Swap)

CAS(Compare-And-Swap)는 공유 데이터 변경 시 락을 사용하지 않고, 원자적으로 값을 갱신하는 동시성 기법입니다.

<br/>

> CAS 연산 방식

CAS 연산은 보통 세 개의 값을 사용합니다.

- 현재 값 (V, Value): 변경하려는 메모리 주소에 저장된 현재 값.
- 기대 값 (E, Expected): 우리가 예상하는 값 (현재 값이 이 값일 것으로 기대함).
- 새로운 값 (N, New Value): 성공 시 변경할 값.

> 작동 원리

```text
if (현재 값 V == 기대 값 E) {
    → V를 새로운 값 N으로 변경 (성공)
} else {
    → 다른 스레드가 값을 변경했으므로 실패, 다시 시도
}
```

<br/>

### CAS를 활용한 코드 예제 (Java의 AtomicInteger 사용)

자바에서는 AtomicInteger 같은 클래스에서 CAS 연산을 제공하며, 내부적으로 Unsafe.compareAndSwapInt()를 사용합니다.

```java
import java.util.concurrent.atomic.AtomicInteger;

public class CASExample {
    public static void main(String[] args) {
        AtomicInteger atomicValue = new AtomicInteger(100); // 초기값 100

        // CAS를 사용한 값 변경
        boolean success = atomicValue.compareAndSet(100, 200); // 기대 값이 100이면 200으로 변경

        System.out.println("CAS 성공 여부: " + success); // true
        System.out.println("현재 값: " + atomicValue.get()); // 200
    }
}
```

<br/>

### CAS 연산의 문제점

- ABA 문제
    - A → B → A로 변경되면 CAS가 성공하지만, 사실 데이터가 바뀐 것을 인지하지 못함.
    - 해결 방법: AtomicStampedReference 사용 (타임스탬프 추가).
- 스핀락(Spin-lock) 문제
    - CAS 실패 시 계속 재시도해야 하므로, 경쟁이 심하면 CPU 사용량 증가.
    - 해결 방법: 락 기반 동기화 사용 (ReentrantLock).

<br/>

### Atomic 클래스 내부 동작 과정

1. Unsafe 클래스를 이용해 메모리에서 value 값이 위치한 offset(주소) 을 찾음.
2. compareAndSwapInt()로 기존 값과 기대 값이 같은지 비교.
3. 같으면 새로운 값으로 변경하고, 다르면 다시 시도(Spin-loop).

<br/>

### Atomic 클래스 내부 구현 방식

> CAS 기반 원자적 연산

- Atomic 클래스들은 CAS 연산을 활용해 값을 업데이트합니다.
- 이를 통해 스레드 간 경쟁이 있어도 값이 안전하게 변경됩니다.

   ```java
   public final int incrementAndGet() {
       return unsafe.getAndAddInt(this, valueOffset, 1) + 1;
   }
   ```

<br/>

> Unsafe 클래스 활용

- Atomic 클래스들은 sun.misc.Unsafe를 사용하여 메모리 접근과 CAS 연산을 수행합니다.

  ```java
  private static final Unsafe unsafe = Unsafe.getUnsafe();
  private static final long valueOffset;
  
  static {
      try {
          valueOffset = unsafe.objectFieldOffset
              (AtomicInteger.class.getDeclaredField("value"));
      } catch (Exception ex) { throw new Error(ex); }
  }
  ```

- unsafe.objectFieldOffset()
    - value 변수가 메모리에서 어디에 위치하는지(Offset) 를 가져옴.
- unsafe.compareAndSwapInt()
    - CAS(Compare-And-Swap) 연산을 사용하여 값을 변경.
