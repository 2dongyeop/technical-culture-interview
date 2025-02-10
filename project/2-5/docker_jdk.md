## 프로젝트별 JDK 버전 상이 문제를 해결하기 위해 Docker 컨테이너 환경을 어떻게 구축/운영했나요?

<br/>

> 배경 설명
>

- 우리 서비스에서는 **프로젝트마다 JDK 버전이 다르게 사용**되는 문제가 존재
    - 일부 프로젝트는 **JDK 8**, 다른 프로젝트는 **JDK 17**을 사용
    - 개발 환경과 운영 환경 간의 **JDK 버전 불일치**로 인해 빌드 및 배포 시 이슈 발생
- 이를 해결하기 위해 **Docker 기반의 컨테이너 환경을 구축**하여 JDK 버전을 통합적으로 관리

<br/>

> Dockerfile 작성
>

```docker
FROM openjdk:8-jdk-alpine
# FROM openjdk:17-jdk-alpine # JDK 17 사용시

ENV JAR_FILE={PROJECT_NAME}.jar
ENV JAR_PATH={PROJECT_PATH}
ENV PORT={PROJECT_PORT}
ENV JAVA_OPTS="-Xms2048m -Xmx2048m 과 같은 JVM Option..."

# JAR_FILE을 Docker 컨테이너 내부에 복사
# 개발 서버와 Docker 컨테이너 내부 위치를 헷갈리지 않기 위해 동일하게 지정.
COPY ${JAR_FILE} ${JAR_PATH}/${JAR_FILE}

# Docker 컨테이너 내에서 Spring Boot 프로젝트가 사용할 포트. 헷갈리지 않도록 동일하게 지정.
EXPOSE ${PORT}

ENTRYPOINT ["sh", "-c", "java ${JAVA_OPTS} -jar ${JAR_PATH}/${JAR_FILE}"]
```