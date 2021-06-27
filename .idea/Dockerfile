FROM ubuntu:18.04
RUN apt-get update; \
    apt-get install -y maven; \
    apt-get install -y default-jdk; \
    apt-get install -y git; \
RUN wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.46/bin/apache-tomcat-9.0.46.tar.gz -O /tmp/tomcat.tar.gz
RUN cd /tmp && tar xvfz tomcat.tar.gz
RUN cp -Rv /tmp/apache-tomcat-9.0.46 /usr/local/tomcat/
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git /home/App42PaaS-Java-MySQL-Sample
WORKDIR /home/App42PaaS-Java-MySQL-Sample
RUN mvn package
RUN cp /home/App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war /usr/local/tomcat/apache-tomcat-9.0.46/webapps
EXPOSE 8080
CMD ["/opt/tomcat/bin/catalina.sh", "run"]