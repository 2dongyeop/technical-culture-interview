## HTTP 1.1, HTTP/2, HTTP/3

<br/>

> **HTTP 1.1**
>

- **기반 프로토콜:** TCP
- **특징:**
    - 기본적인 **요청-응답(Request-Response) 방식**
    - 하나의 요청이 끝나야 다음 요청을 처리할 수 있는 **단일 연결 방식**
    - **HOL(Head-of-Line) 블로킹 문제 발생** → 하나의 요청이 지연되면 다른 요청도 대기
    - `keep-alive` 옵션으로 **연결 유지 가능하지만 한 번에 하나의 요청만 처리 가능**
- **단점:** 속도가 느리고 네트워크 리소스를 비효율적으로 사용

<br/>

> **HTTP/2**
>

- **기반 프로토콜:** TCP
- **특징:**
    - **멀티플렉싱(Multiplexing) 지원** → 하나의 연결에서 **동시에 여러 개의 요청 처리 가능**
    - **헤더 압축(HPACK) 지원** → HTTP 헤더 크기를 줄여 네트워크 비용 감소
    - **서버 푸시(Server Push) 지원** → 클라이언트 요청 없이도 서버가 리소스를 미리 전송 가능
- **장점:** 성능 향상(동시 요청 처리), 네트워크 효율 증가
- **단점:** TCP 기반이라 여전히 **HOL 블로킹 문제 발생 가능**

<br/>

> **HTTP/3**
>

- **기반 프로토콜:** **UDP (QUIC)**
- **특징:**
    - TCP 대신 **UDP 기반 QUIC 프로토콜 사용** → 더 빠른 연결 확립 (0-RTT 핸드셰이크)
    - **HOL 블로킹 문제 완전 해결** → 패킷 손실 시에도 개별 스트림만 영향받음
    - 연결이 끊어져도 **연결 재사용(Connection Migration) 가능**
      (예: Wi-Fi → LTE 전환 시에도 끊기지 않음)
    - **암호화 기본 적용** (TLS 1.3 포함)
- **장점:** 지연 시간 최소화, 네트워크 최적화, 보안 강화
- **단점:** UDP 기반이므로 기존 방화벽 및 네트워크 장비에서 호환성 문제 발생 가능