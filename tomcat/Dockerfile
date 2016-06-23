#Version: tomcat 8.5.3
FROM morrowind/centos:7.2
MAINTAINER Morro Wind "imorrowind@hotmail.com"

ENV TOMCAT-MAJOR 8
ENV TOMCAT_VERSION 8.5.3

ENV JAVA_HOME /usr/local/jdk
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$JAVA_HOME/bin:$PATH
COPY jdk1.8.0_02/ /usr/local/jdk/
COPY apache-tomcat-8.5.3/ /usr/local/tomcat/
#ADD server.xml /usr/local/tomcat/conf/server.xml
RUN useradd tomcat
USER tomcat
WORKDIR $CATALINA_HOME
EXPOSE 8080
CMD ["daemon.sh", "run"]
