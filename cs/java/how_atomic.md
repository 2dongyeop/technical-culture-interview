## Atomic은 Thread-Safe한 클래스인지? 그리고 내부적으로 어떻게 구현되어 있는지 아시나요?

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
