#Version: Centos 7.2 CST
FROM centos:latest
MAINTAINER Morro Wind "imorrowind@hotmail.com"
RUN yum -y -q upgrade
#update system timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
#update application timezone
RUN echo "Asia/Shanghai" >> /etc/timezone
