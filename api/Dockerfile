# FROM maven:3.5.3-jdk-8-alpine
# COPY pom.xml .
# COPY src /src
# RUN  mvn -B -f pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve \
#      && mvn -B -s /usr/share/maven/ref/settings-docker.xml package -DskipTests \
#      && adduser -Dh /home/gordon gordon
# COPY --from=build /target/ddev-0.0.1-SNAPSHOT.jar /home/gordon/ddev-0.0.1-SNAPSHOT.jar
# CMD  java -jar /home/gordon/ddev-0.0.1-SNAPSHOT.jar --spring.profiles.active=postgres

FROM maven:latest AS build
COPY pom.xml .
COPY src /src
RUN  mvn -B -f pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve \
     && mvn -B -s /usr/share/maven/ref/settings-docker.xml package -DskipTests

FROM openjdk:8u151-jre-alpine3.7
RUN  adduser -Dh /home/gordon gordon
COPY --from=build /target/ddev-0.0.1-SNAPSHOT.jar /home/gordon/ddev-0.0.1-SNAPSHOT.jar
CMD  java -jar /home/gordon/ddev-0.0.1-SNAPSHOT.jar --spring.profiles.active=postgres
