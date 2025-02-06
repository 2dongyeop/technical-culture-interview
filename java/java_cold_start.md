## JVM Cold Start 최적화를 위해 어떤 접근 방식을 사용했나요?

1. JVM 옵션 최적화
    1. `-Xms`와 `-Xmx` 값을 동일하게 설정

<br/>

2. JIT 컴파일러 최적화 (= C2 컴파일러 비활성화 = C1 컴파일러만 동작하도록 지정)
    - C1, C2 컴파일러
        - C1 컴파일러 : 빠르게 컴파일 완료하여 애플리케이션의 성능을 향상
        - C2 컴파일러 : 자주 사용하는 코드를 네이티브 코드로 변환하여 성능을 향상
            - → 정교한 최적화 기법을 사용하기에, 컴파일 시간과 리소스 사용이 많아 오버헤드가 발생할 수 있음.

   `java -jar -XX:TieredStopAtLevel=1 {프로젝트이름}.jar`


- https://velog.io/@dongvelop/Spring-Boot-JVM-Cold-Start-%EC%B5%9C%EC%A0%81%ED%99%94%ED%95%98%EA%B8%B0