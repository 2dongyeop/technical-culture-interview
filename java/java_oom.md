## OutOfMemoryError가 발생했을 때, 어떤 방법으로 원인을 분석할 수 있나요?

1. **에러 로그를 통해**  OOM 유형 파악
    - **Java Heap Space:** 힙 메모리 부족 → 객체 누수(Leak) 가능성
    - **GC Overhead Limit Exceeded:** GC가 지나치게 자주 발생 → GC 튜닝 필요
    - **Metaspace:** 클래스 메타데이터 공간 부족 → 동적 클래스 로딩 이슈
    - **Direct Buffer Memory:** 네이티브 메모리 누수 → NIO 또는 외부 라이브러리 문제
    - **Unable to create new native thread:** 스레드 수 제한 초과 → Thread Leak 가능성

<br/>

2. **Heap Dump 분석** → 메모리 누수 원인 찾기
    - Heap Dump 생성을 위한 JVM 옵션
        - `XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/path/to/dump.hprof`
    - **분석 포인트:**
        - 가장 많은 메모리를 차지하는 객체는?
        - `GC Root`와 연결된 객체가 계속 유지되는 이유는?
        - **String** 객체가 과도하게 쌓여 있다면, 불필요한 캐시나 로그 버퍼 확인

<br/>

3. **GC 로그 분석** → 메모리 회수/할당 패턴 확인.. 혹은 JVM 힙메모리 옵션 검토..(크기가 적절한지)
    - GC Log 활성화를 위한 JVM 옵션
        - `Xlog:gc*:file=/path/to/gc.log:time,uptime,level,tags`

<br/>

4. **스레드/네이티브 메모리 검사** → 리소스 누수 여부 확인
    - 네이티브 메모리 추적(NMT) 활성화를 위한 JVM 옵션
        - `XX:NativeMemoryTracking=summary`

<br/>

5. **코드/설정 리뷰** → 캐시, 리스너, 외부 라이브러리 점검
    - `Static` 컬렉션에 객체를 지속적으로 저장하는 코드
    - 캐시 무한 확장 (`Map`에 무제한 데이터 적재)
    - 이벤트 리스너, 콜백 미제거
    - **JVM 옵션 검토 (e.g.** `Xmx`, `Xms` 설정이 과도하게 낮지 않은지)