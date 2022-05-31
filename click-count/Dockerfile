FROM maven:3.8-jdk-8-slim AS builder

RUN mkdir /opt/click-count
COPY . /opt/click-count
WORKDIR /opt/click-count
RUN mvn clean install


FROM apache/flink:1.14.4-scala_2.12-java8

WORKDIR /opt/flink/bin
COPY --from=builder /opt/click-count/target/click-count-*.jar /opt/ClickCountJob.jar
