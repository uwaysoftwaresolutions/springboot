# springboot
==========Initial project setup===========================
https://spring.io/guides/gs/spring-boot-docker/

Download and unzip the source repository for this guide, or clone it using Git:
cd into gs-spring-boot-docker/complete
C:\Labs\SpringBootProjects\gs-spring-boot-docker-master\complete

==============Build Using maven===========================
Build the project using maven:
mvnw clean package

===============Containerize It============================

Change Dockerfile as below:
FROM openjdk:8-jdk-alpine
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]

=====================Build and Run the Docker===============
docker build -t springio/gs-spring-boot-docker .
docker run -p 8080:8080 springio/gs-spring-boot-docker


================Access Application==========================
http://localhost:8080
