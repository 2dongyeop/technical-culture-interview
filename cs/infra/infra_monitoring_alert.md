## 모니터링 및 Alert 구축 시 고려사항

> **모니터링 목표 설정**
>

- **목표 정의**:
    - 시스템에서 모니터링하고자 하는 핵심 항목을 정의해야 합니다.
    - 예를 들어, **CPU 사용률, 메모리 사용량, 네트워크 트래픽, 디스크 I/O**와 같은 자원 모니터링뿐만 아니라, **애플리케이션의 응답 시간, API 호출 성공/실패율**, **사용자 경험** 등을
      포함할 수 있습니다.
- **서비스 수준 목표(SLO)**:
    - 비즈니스 및 시스템의 중요도에 따라 모니터링 항목에 대한 **서비스 수준 목표(SLO)**와 **서비스 수준 지표(SLI)**를 설정해야 합니다.
    - 예를 들어, 응답 시간이 2초를 넘지 않도록 하는 것이 하나의 SLO가 될 수 있습니다.

<br/>

> **모니터링 지표 선정**
>

- **시스템 지표**: 서버 상태, 네트워크 상태, 디스크 사용량, CPU 부하 등을 실시간으로 모니터링합니다. 예를 들어, `Prometheus`나 `Zabbix`는 시스템 상태를 추적하고, `Grafana`는
  이를 시각화하는 데 유용합니다.
- **애플리케이션 지표**: 애플리케이션의 **응답 시간, API 호출 성공/실패, 오류율, 쓰기/읽기 처리량**, **메모리 누수** 등을 추적하여, 애플리케이션 성능에 대한 통찰을 얻습니다.
- **비즈니스 지표**: 예를 들어 **사용자 활동, 결제 처리, 페이지 뷰** 등의 지표도 포함하여, 시스템이 비즈니스에 미치는 영향을 추적할 수 있습니다.

<br/>

> **알림(Alert) 설정**
>

- **알림 기준 설정**:
    - 알림은 적절한 임계값을 기준으로 설정해야 하며, 그 기준을 설정할 때는 **경고 임계값**, **시간 범위**, **우선순위** 등을 잘 정의해야 합니다.
    - e.g. **CPU 사용률이 90%를 넘으면 경고**, **디스크 용량이 80%를 넘으면 알림**을 설정
- **알림의 정확도**:
    - 너무 자주 알림이 발생하면 경고 피로감이 생길 수 있기 때문에 **이상 징후가 지속되는 경우**에만 알림을 발생하도록 설정합니다.
    - 예를 들어, **1분 이상 임계값을 초과했을 때만 경고**하도록 하는 것이 효과적입니다.
- **알림 대상 그룹 설정**:
    - 알림을 받는 대상 그룹을 명확히 정의해야 합니다.
    - 예를 들어, **시스템 관리자**, **개발자**, **운영팀** 등 각 팀에 적합한 알림을 설정하여, 필요에 따라 빠르게 대응할 수 있도록 합니다.
- **알림 채널 설정**:
    - 알림을 받을 방법도 중요합니다.
    - **이메일, Slack, SMS, PagerDuty** 등 다양한 채널을 통해 알림을 받을 수 있으며,
      긴급한 상황은 **SMS**나 **전화** 등 더 즉각적인 방법을 사용할 수 있습니다.

<br/>

> **알림 심각도 및 우선순위 설정**
>

- **알림의 심각도 분류**:
    - 알림의 심각도를 **Critical, Warning, Info** 등으로 나누어, 각 알림에 대한 대응 우선순위를 설정해야 합니다.
    - 예를 들어, **서비스가 완전히 중단되면 Critical**, **시스템 부하가 높지만 정상적으로 동작** 중이면 **Warning**으로 설정합니다.
- **자동화된 대응 시스템 구축**:
    - 특정 알림이 발생했을 때 **자동으로 시스템을 재시작하거나**, **리소스를 확장하거나**, **경고 메시지를 팀에 전송하는 자동화**를 설정하여 문제를 빠르게 해결할 수 있도록 합니다.

<br/>

> **시각화 및 대시보드**
>

- **대시보드 구성**:
    - 다양한 지표와 알림을 시각적으로 한눈에 파악할 수 있도록 **Grafana, Kibana**와 같은 대시보드 툴을 활용하여 시각화합니다.
    - 이를 통해 시스템 상태를 한눈에 파악할 수 있고, 문제가 발생한 시점과 원인을 빠르게 파악 가능
- **상태 페이지 제공**:
    - **웹 대시보드**나 **상태 페이지**를 외부에 제공하여 서비스의 상태나 정상/비정상 여부를 모니터링할 수 있게 합니다.

<br/>

> **데이터 수집 및 저장**
>

- **모니터링 데이터의 저장 기간**:
    - 데이터를 얼마나 오래 저장할 것인지에 대해 고려해야 합니다.
    - **단기(예: 1주일), 중기(1개월), 장기(1년)** 저장 기간을 설정하고,
      필요에 따라 **샘플링** 또는 **집계(aggregation)** 기술을 사용하여 저장 공간을 최적화합니다.
- **데이터의 정합성**:
    - 수집된 데이터가 정확하고 신뢰할 수 있도록 하여, 이후 문제 해결 시 유용하게 활용될 수 있도록
    - e.g., 로그 데이터에서 불필요한 정보나 잘못된 정보를 필터링합니다.

<br/>

> **성능 최적화 및 비용 관리**
>

- **리소스 사용 최적화**:
    - 수집되는 데이터 양이 많아지면 **메모리, CPU** 등의 자원 소비가 커질 수 있습니다.
    - 모니터링 시스템을 최적화하여 시스템에 미치는 영향을 최소화하고, 성능을 저하시키지 않도록
- **비용 관리**:
    - 클라우드 기반 모니터링 시스템을 사용할 때는 **데이터 전송 비용, 저장 비용**이 발생하므로,
    - 이에 대한 비용을 주기적으로 모니터링하고 최적화 방안을 마련합니다.

<br/>

> **스케일링 및 고가용성**
>

- **모니터링 시스템의 확장성**:
    - 시스템이 확장될 경우, 모니터링 시스템도 그에 맞춰 확장되어야 합니다.
    - 예를 들어, **Prometheus**와 같은 시스템은 여러 서버를 모니터링할 때 **샤딩(sharding)**을 통해 수평 확장이 가능합니다.
- **고가용성**:
    - 중요한 모니터링 및 알림 시스템은 **고가용성(HA)** 구성을 통해 장애 시에도 서비스가 지속될 수 있도록 구성해야 합니다.
    - 예를 들어, **Prometheus의 HA 구성을 위한 두 개 이상의 서버 운영**이나 **alertmanager 이중화** 등이 필요할 수 있습니다.

<br/>

> **문서화 및 교육**
>

- **모니터링 시스템의 문서화**:
    - 모니터링 및 알림 시스템에 대한 **문서화**가 필요합니다.
    - 누가 어떤 데이터를 모니터링하고, 알림의 기준이 무엇이며, 발생한 알림에 어떻게 대응할지에 대한 명확한 문서가 있어야 합니다.
- **팀 교육**:
    - 알림을 받는 사람들에 대해 시스템에 대한 교육이 필요합니다.
    - 알림이 왔을 때, **각각의 알림이 의미하는 바와 대응 절차**를 명확히 알고 있어야 효율적으로 문제를 해결할 수 있습니다.