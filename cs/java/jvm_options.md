## 알아두면 좋을 JVM Option

### 1. 메모리 관련

```shell
# Heap 크기 설정
-Xms2g -Xmx2g
```

- Xms → 초기 Heap 크기
- Xmx → 최대 Heap 크기
- [Xms와 Xmx를 동일하게 설정하는 이유](cs/java/java_jvm_xmx_xms.md)

<br/>

```shell
# 메타스페이스 크기 설정 (JDK 8~)
-XX:MetaspaceSize=256m -XX:MaxMetaspaceSize=512m
```

- JDK 8부터 PermGen이 제거되고 Metaspace로 변경됨.
- Metaspace 크기를 제한하여 클래스 메타데이터 누수 방지 가능.
- Metaspace 크기를 제한해야 하는 이유
    - Metaspace는 기본적으로 JVM 프로세스가 사용할 수 있는 메모리를 전부 사용 가능
    - 즉, 제한 없이 계속 커질 수도 있기 때문에, 메모리 누수를 방지하려면 최대 크기를 설정하는 것이 중요

<br/>

```shell
# 다이렉트 메모리 사이즈 설정
-XX:MaxDirectMemorySize=20M 
```

- 다이렉트 메모리 : JVM 프로세스가 I/O 작업을 위해 사용하는 바이트 배열 저장 위치 → 네이티브 메모리에 속함
- 기본값은 -Xmx로 설정한 힙 메모리 크기와 동일

<br/>

```shell
# 네이티브 메모리 사용량 추적 활성화
-XX:NativeMemoryTracking=summary
```

- 이 옵션을 사용하면 JVM의 네이티브 메모리(힙 이외의 메모리) 사용량을 추적 가능.
- 모든 옵션은 다음과 같다. [off/summary/detail]

<br/>

```shell
# Young 영역 크기 설정
-XX:NewSize=<young size>[unit]
```

- Oracle 지침에 의하면 Young 영역의 최소 크기는 1310MB이고 , 최대 크기는 무제한으로 권장하고 있다.

<br/>

### 2. GC 튜닝

```shell
# GC 종류 설정 (JDK 11~21 기준)
# G1GC (JDK 9+ 기본)
-XX:+UseG1GC 

# ZGC (JDK 11+)
-XX:+UseZGC

# Shenandoah (JDK 12+)
-XX:+UseShenandoahGC
```

- G1GC → 일반적인 서버 환경에 적합, 균형 잡힌 GC
- ZGC → 저지연(low-latency) GC, 대용량 Heap (100GB+) 사용 시 유리
- Shenandoah → 짧은 GC Pause, 지연이 중요한 애플리케이션에 적합

<br/>

```shell
# GC 로그 활성화 (JDK 9+ 기준)
-Xlog:gc*:file=gc.log:time,uptime,level,tags
```

- GC 로그 확인으로 메모리 문제 진단 가능
- gc+heap=debug → GC 힙 변화 로그 출력

<br/>

### 3. CPU & 성능 최적화

```shell
# JIT 컴파일러 제어 (GraalVM 사용 가능)
-XX:+UnlockExperimentalVMOptions -XX:+UseJVMCICompiler
```

- Graal JIT 활성화로 성능 향상 (JDK 17+ 추천)

<br/>

### 4. 디버깅 & 트러블슈팅

```shell
# OOM 발생 시 덤프 생성
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/path/to/dump
```

- OOM 발생 시 자동으로 Heap Dump 저장
- 덤프 파일을 분석해서 메모리 누수 파악 가능

<br/>

```shell
# JFR (Java Flight Recorder) 사용
-XX:+FlightRecorder -XX:StartFlightRecording=filename=recording.jfr,duration=60s
```

- JVM 성능 데이터 수집 (CPU, GC, 메모리, 스레드 등)
- jfr 파일을 JDK Mission Control (JMC) 로 분석

<br/>

#### 5. 컨테이너 환경에서 유용한 옵션

```shell
# 컨테이너 리소스 제한 준수 (JDK 10+)
-XX:+UseContainerSupport
```

- 컨테이너 내에서 CPU 및 메모리 제한을 준수하도록 설정

<br/>

#### 6. 기타

```shell
-XX:+UseG1GC: Enables the Garbage-First (G1) garbage collector, which is designed for applications with large heaps and limited Garbage Collection latency requirements.
-XX:+UseZGC: Enables the Z Garbage Collector, which is designed for applications requiring low latency without sacrificing throughput.
-XX:+UseShenandoahGC: Enables the Shenandoah Garbage Collector, which aims to reduce Garbage Collection pause times by performing more garbage collection work concurrently with the application threads.
-XX:+UseParallelGC: Enables the parallel garbage collector for the young generation.
-XX:NewRatio=<ratio>: Sets the ratio between the young and old generation sizes. For example, -XX:NewRatio=3 means the old generation will be three times the size of the young generation.
-XX:SurvivorRatio=<ratio>: Sets the ratio of the eden/survivor space size. Decreasing this ratio can increase the size of the survivor spaces.
-XX:MaxGCPauseMillis: Sets a target for the maximum Garbage Collector pause time. This is a soft goal, and the Java Virtual Machine will make its best effort to achieve it.
-XX:+UseSerialGC: Enables the serial garbage collector, which uses a single thread for garbage collection and is suitable for small applications with low memory footprint.
-XX:ParallelGCThreads: Sets the number of threads used during parallel phases of the garbage collectors. The default value varies with the platform on which the Java Virtual Machine is running.
-XX:ConcGCThreads: Number of threads concurrent garbage collectors will use. The default value varies with the platform on which the Java Virtual Machine is running.
-XX:InitiatingHeapOccupancyPercent: Percentage of the entire heap occupancy to start a concurrent Garbage Collection cycle.
-XX:+HeapDumpOnOutOfMemoryError: Tells the Java Virtual Machine to generate a heap dump when it throws an OutOfMemoryError.
-XX:+PrintGCDetails: Prints detailed output at each garbage collection. Useful for tuning the garbage collector.
-XX:+PrintGCDateStamps: Adds a date stamp to each garbage collection event printed in the logs.
-XX:+PrintHeapAtGC: Prints detailed information about the heap before and after Garbage Collection.
-XX:+PrintGCApplicationStoppedTime: Prints how much time was spent in Garbage Collection pauses, helping in identifying pause times due to Garbage Collection.
-XX:+PrintGCApplicationConcurrentTime: Reports the time spent outside of garbage collection (i.e., the time the application was running).
-XX:+UseCodeCacheFlushing: Allows the Java Virtual Machine to flush the code cache when it is full, which can help prevent the Java Virtual Machine from shutting down if the code cache fills up.
```
