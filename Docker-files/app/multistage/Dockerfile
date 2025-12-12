FROM maven:3.9.11-eclipse-temurin-21-noble AS BUILD_IMAGE
RUN git config --global http.sslVerify false

RUN git clone https://github.com/T0KaG/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:10-jdk21

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
