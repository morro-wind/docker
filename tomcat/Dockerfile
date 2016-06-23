#Version: tomcat 0.0.1
FROM centos:latest
MAINTAINER Morro Wind "morro-wind@hotmail.com"
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/locatime
ENV TOMCAT_0.0.1

ENV JAVA_HOME /usr/local/jdk
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$JAVA_HOME/bin:$PATH
COPY jdk1.8.0_02/ /usr/local/jdk/
COPY apache-tomcat-8.5.3/ /usr/local/tomcat/
ADD server.xml /usr/local/tomcat/conf/server.xml
