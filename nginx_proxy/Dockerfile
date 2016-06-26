#Version: 0.0.1
FROM morrowind/centos
MAINTAINER Morro Wind "imorrowind@hotmail.com"
ENV NGINX_VERSION 1.10.1
RUN yum -y install gcc pcre-devel zlib-devel openssl-devel openssl 
ADD http://nginx.org/download/nginx-1.10.1.tar.gz
RUN cd nginx-1.10.1
#modify nginx version and name
RUN sed -i '/NGINX_VERSION/{s/1.10.1/proxy/g}' src/core/nginx.h && sed -i '/NGINX_VER/{s/nginx/izj/g}' src/core/nginx.h
RUN ./configure 
RUn useradd nginx
USER nginx
ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
EXPOSE 80
