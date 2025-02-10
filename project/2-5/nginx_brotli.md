## Nginx Brotli 압축 방식을 적용한 이유가 무엇인가요?

<br/>

> **Brotli란?**
>

- Brotli는 Google이 개발한 **고성능 압축 알고리즘**으로,
- Gzip보다 **압축률이 높고, 속도가 빠름** → 웹 페이지 로딩 속도 향상

<br/>

> **Brotli vs Gzip 비교**
>

| 알고리즘       | 압축률                           | 압축 속도 | 지원 브라우저                       |
|------------|-------------------------------|-------|-------------------------------|
| **Brotli** | **높음 (Gzip보다 약 15~20% 더 좋음)** | 빠름    | Chrome, Firefox, Edge, Safari |
| **Gzip**   | 보통                            | 보통    | 대부분 지원                        |

<br/>

> Brotli 압축 적용시 고려사항
>

1. **Brotli 압축 수준 조정 (CPU 사용량 vs 성능)**
    - Brotli는 Gzip보다 **압축률이 높지만 CPU 사용량이 증가할 수 있음.**
    - 압축 수준(`brotli_comp_level`)을 **적절하게 설정**해야 함.
    - **권장 설정**

        ```
        brotli_comp_level 5;  # 기본값은 6, CPU 리소스를 고려해 4~6 추천
        ```


2. 클라이언트 지원 여부 확인
    - 브라우저 또는 프록시가 **Brotli를 지원하지 않을 수도 있음.**
    - `content-encoding: br` 을 지원하지 않는 경우, Gzip이나 원본 파일을 제공해야 함.
    - **Brotli & Gzip 함께 적용**
        - Brotli를 지원하는 클라이언트는 Brotli 사용
        - 지원하지 않는 경우 Gzip으로 자동 fallback

        ```
        brotli on;
        brotli_static on;
        brotli_types text/plain text/css application/javascript application/json image/svg+xml;
        
        gzip on;
        gzip_types text/plain text/css application/javascript application/json image/svg+xml;
        ```


3. **모바일 네트워크 환경 고려**
    - Brotli는 압축률이 뛰어나지만, 일부 저사양 디바이스에서는 **압축 해제 속도가 느릴 수 있음.**
    - 네트워크 속도가 빠른 환경에서는 **오히려 Gzip보다 성능이 나쁠 수도 있음.**