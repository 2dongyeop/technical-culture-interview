## Spring Cloud Config Server의 장단점

> 장점
>

1. **중앙 집중식 설정 관리**
    - 여러 마이크로서비스의 환경 설정을 **Config Server에서 통합 관리**.
    - 환경별 설정(dev, staging, prod) 변경이 용이함.
2. **실시간 설정 변경 가능**
    - Spring Cloud Bus(Kafka, RabbitMQ)와 연계하면 **애플리케이션 재시작 없이 설정 변경 가능**.
3. **버전 관리 가능**
    - 설정 파일을 Git 등에 저장하면 변경 이력을 관리할 수 있음.

<br/>

> **단점**
>

1. **최초 애플리케이션 기동 시 Config Server 의존성**
    - 초기 기동 시 Config Server에서 설정을 가져와야 하므로, Config Server가 응답하지 않으면 서비스가 정상적으로 동작하지 않을 수 있음.
    - 해결책: **Fail Fast 옵션 비활성화** 및 로컬 캐싱 활용.