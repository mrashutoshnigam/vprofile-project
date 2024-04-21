FROM openjdk:11 as BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/mrashutoshnigam/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn clean install

FROM tomcat:9-jre11-slim
LABEL "Project"="VProfile"
LABEL "Author"="Imran"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]