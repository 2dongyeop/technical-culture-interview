## AWS RDS 모니터링 구축 시,AWS CloudWatch 대신 Percona rds_exporter를 선택한 이유

**1. 비용 절감**

- **CloudWatch는 생성한 경보 및 로그당 과금이 발생**하며, 특히 **Custom Metrics**(예: Enhanced Monitoring)나 긴 데이터 보존 기간을 요구할 경우 비용이 크게 증가함.
- **rds_exporter는 Prometheus 기반**으로 동작하며, 자체적인 모니터링 스택을 운영하면 추가 비용 없이 상세한 메트릭을 수집 가능.

<br/>

**2. 더 세밀한 모니터링**

- CloudWatch는 기본적으로 제공하는 **RDS 지표(예: CPUUtilization, FreeableMemory, ReadIOPS)**만 활용 가능하고, 세부적인 데이터는 제한적임.
- 반면, rds_exporter는 **MySQL Performance Schema, InnoDB 상태, Replication Delay, Query Performance** 등 DB 내부 상태를 상세히 모니터링
  가능.

<br/>

**3. Prometheus 및 Grafana와의 연동**

- **Prometheus와 Grafana를 이미 운영 중**이라면, 동일한 모니터링 시스템에서 통합적으로 RDS를 감시할 수 있음.
- **Custom Dashboard**를 활용해 특정 지표를 조합하여 서비스 특화된 모니터링 가능.

<br/>

**4. 실시간 지표 수집 및 경고 시스템 강화**

- CloudWatch는 기본적인 알람 기능을 제공하지만, **Scraping Interval이 1분 또는 5분**으로 제한됨.
- rds_exporter는 **Prometheus Pull 방식**을 사용하여 **10~15초 단위**로 더 빠르게 메트릭을 수집 가능.
- **Grafana Alerting, Alertmanager** 등을 활용하여 Slack, PagerDuty 등과 연계한 경고 시스템 구축 가능.