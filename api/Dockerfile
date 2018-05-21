FROM maven:3.5.3-jdk-8-alpine
RUN  mvn -B -f pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve \
     && mvn -B -s /usr/share/maven/ref/settings-docker.xml package -DskipTests \ 
     && adduser -Dh /home/gordon gordon
RUN  java -jar <path to jar file>/ddev-0.0.1-SNAPSHOT.jar \ --spring.profiles.active=postgres
