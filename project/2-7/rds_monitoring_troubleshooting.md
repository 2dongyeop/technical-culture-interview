## AWS RDS 모니터링 시스템 구축 과정에서 문제점과 해결방법

> **rds_exporter의 데이터 수집 범위 및 성능 이슈**

- 내용 요약
    - rds_exporter가 제공하는 **기본 메트릭**이 CloudWatch보다 풍부하지만, **정확히 어떤 데이터까지 수집할 수 있는지** 확인이 필요했음.
    - **쿼리 실행 성능 부담**이 문제될 가능성이 있어, RDS의 성능에 영향을 주지 않도록 해야 함.
- **해결 과정**
    - 공식 문서와 GitHub을 참고하여 **기본적으로 수집하는 메트릭 리스트**를 분석.
    - `-collect.*` 옵션을 조정하여 **불필요한 메트릭 비활성화** → 과도한 쿼리 실행 방지.
    - **Scraping Interval을 15~30초**로 설정하여, RDS 성능에 영향을 최소화하면서도 실시간 모니터링 가능하도록 조정.

<br/>

> **Prometheus의 스토리지 용량 문제**

- 내용 요약
    - Prometheus는 시계열(Time-Series) 데이터를 저장하기 때문에, RDS 모니터링 메트릭이 많아지면 **디스크 사용량이 급증**할 가능성이 있음.
    - 데이터 보존 기간이 길어질수록 저장 공간과 쿼리 성능 저하 문제가 발생할 수 있음.
- **해결 과정**
    - Prometheus의 **Retention Period**를 7일로 제한 (`-storage.tsdb.retention.time=7d`).

<br/>

> **중복 메트릭 수집 이슈**

- 내용 요약
    - rds_exporter는 내부적으로 Cloudwatch API를 이용하는데
    - AWS CloudWatch API는 메트릭을 60초마다 갱신하지만, rds_exporter를 10초마다 메트릭을 조회하여 **중복된 메트릭을 가져오면서 불필요한 비용을 발생시키는 문제 발생**
- 해결 과정
    - **원본 소스인 점을 이용하여 원본 소스 코드로부터 주기를 조정하여 중복 조회를 해결하고, 불필요한 메트릭은 조회하지 않도록 수정**