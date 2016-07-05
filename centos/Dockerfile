#Version: Centos 7.2 CST
FROM centos:latest
MAINTAINER Morro Wind "imorrowind@hotmail.com"
RUN yum -y -q upgrade && yum clean all
#update system and application timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo "Asia/Shanghai" >> /etc/timezone
