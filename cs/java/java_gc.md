## GC 별 특징 및 구조, 동작 과정

1. GC 정의
    - 더 이상 사용되지 않는 객체를 자동으로 메모리에서 제거하여, 메모리 관리를 자동화하는 메커니즘
    - GC의 주요 목표는 **힙 메모리**를 관리하고, 메모리 누수 및 성능 저하를 방지하는 것

<br/>

1. JVM 메모리 구조
    - GC가 동작하는 주된 공간은 **힙(Heap)** 메모리
    - 힙 메모리는 객체가 할당되는 영역으로, 일반적으로 세 가지 영역으로 나눔
        - **Young Generation**: 새로운 객체들이 생성되는 곳.
            - Young Generation은 **Eden Space**와 두 개의 Survivor Spaces (S0, S1)로 구성.
            - 이 영역에서 객체는 대부분 단기적으로만 존재합니다.
    - **Old Generation (Tenured Generation)**: 장기 생애를 가진 객체들이 이동하는 공간.
        - Young Generation에서 살아남은 객체들이 이 영역으로 이동
    - **Permanent Generation / Metaspace**: 클래스 메타데이터, JIT 컴파일된 코드 등의 메모리 공간
        - 자바 8부터는 **Metaspace**로 대체

<br/>

1. GC 종류
    1. G1 (Garbage First) GC
        - **애플리케이션의 성능과 힙 메모리의 크기**를 모두 고려하여 효율적인 GC를 제공합니다.
        - G1 GC는 Young Generation과 Old Generation을 모두 **분할**하여 작은 **GC 작업을 여러 번 수행**하여 전체 GC 시간을 분배하고 관리합니다.
        - **설정**: `XX:+UseG1GC`
    2. **ZGC (Z Garbage Collector)**
        - 저지연을 목표로 설계된 GC로, GC 동안 애플리케이션의 멈춤 시간을 극도로 짧게 만듭니다.
        - **Large Heap**(대형 힙)에서도 효율적으로 동작할 수 있으며, 실시간 요구가 있는 시스템에 적합합니다.
        - **설정**: `XX:+UseZGC`