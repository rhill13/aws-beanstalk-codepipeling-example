# BUILD STAGE
FROM maven:3.8.3-jdk-11-slim
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

# PACKAGE STAGE
FROM openjdk:11-jre-slim
COPY --from=0 /home/app/target/spring-docker.jar /usr/local/lib/spring-docker.jar
EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "/usr/local/lib/spring-docker.jar" ]