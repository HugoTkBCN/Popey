FROM maven:3.5-jdk-8-alpine AS builder

COPY . /home/.

WORKDIR /home/

RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:8-jre-alpine

COPY --from=builder /home/ /home/.  

WORKDIR /home/target

CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]