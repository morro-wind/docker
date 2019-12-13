# Application example
# Build argument
# build --build-arg APP_NAME=example --build-arg DOMAIN_NAME=example.domain.com --build-arg REDIS_HOST=redisip \
# --build-arg MQ_HOST=mqip --build-arg TOMCAT_CONF=context.xml --no-cache=true .
FROM tomcat:7.0.96-jdk7-alpine
LABEL maintainer=""
ARG APP_NAME
ARG DOMAIN_NAME
ARG REDIS_HOST
ARG MQ_HOST
ARG TOMCAT_CONF=${TOMCAT_CONF:-context.xml}
RUN set -ex; \
    echo JAVA_OPTS="$JAVA_OPTS -server -Xms2000m -Xmx2000m -Xmn1000m -Xss512k -XX:PermSize=500m -XX:MaxPermSize=500m -XX:+UseBiasedLocking  -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:ParallelGCThreads=10 -XX:+CMSParallelRemarkEnabled -XX:CMSFullGCsBeforeCompaction=4 -XX:CMSInitiatingOccupancyFraction=65 -XX:+CMSClassUnloadingEnabled -Dfile.encoding=UTF8 -Dsun.jnu.encoding=UTF8" > /usr/local/tomcat/bin/setenv.sh; \
    rm -rf /usr/local/tomcat/webapps/*; \
    mkdir /opt/applog /opt/setting
COPY setting /opt/setting/

COPY $TOMCAT_CONF /usr/local/tomcat/conf/context.xml
RUN set -ex; \
    cd /opt/setting/quick; \
    sed -i "/^mq.url/{s/localhost/$MQ_HOST/g}" example.properties; \
    sed -i "s/domain.com/$DOMAIN_NAME/g" example.properties; \
    sed -i "s/^redis.sentinel.urls.*$/redis.sentinel.urls=$REDIS_HOST:26379/g" example.properties
VOLUME /opt
COPY ${APP_NAME}.war /usr/local/tomcat/webapps/
