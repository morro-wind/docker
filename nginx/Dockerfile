#Version: 0.0.1
FROM morrowind/centos:7.2
MAINTAINER Morro Wind "imorrowind@hotmail.com"
ENV NGINX_VERSION 1.10.1
ADD nginx.repo /etc/yum.repos.d/nginx.repo
ADD nginx_signing.key nginx_signing.key
RUN rpm --import nginx_signing.key && rm -f nginx_signing.key
RUN yum -y -q update
RUN yum install nginx -y
RUn useradd nginx
USER nginx
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
EXPOSE 80
