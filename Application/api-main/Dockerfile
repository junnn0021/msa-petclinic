# 먼저 Maven을 사용하여 소스 코드를 빌드합니다.
FROM maven:3.6-jdk-11 AS build
WORKDIR /app
COPY . .
RUN mvn clean install

# 빌드된 JAR 파일을 실행 가능한 도커 이미지로 복사합니다.
FROM openjdk:11-jre-slim
COPY --from=build /app/spring-petclinic-api-gateway/target/spring-petclinic-api-gateway-2.1.4.jar /app/app.jar
WORKDIR /app
CMD ["java", "-jar", "app.jar"]
