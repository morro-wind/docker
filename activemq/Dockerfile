#Version: apache-activemq-5.15.10
FROM jdk:8u121-alpine
LABEL maintainer="Morro Wind imorrowind@hotmail.com"

ENV ACTIVEMQ_HOME /usr/local/apache-activemq
ENV PATH $ACTIVEMQ_HOME/bin:$PATH
ENV ACTIVEMQ_VERSION 5.15.10

RUN \
        wget https://www.apache.org/dist/activemq/${ACTIVEMQ_VERSION}/apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz; \
        wget https://www.apache.org/dist/activemq/${ACTIVEMQ_VERSION}/apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz.sha512; \
        set -ex ;\
        sha512sum -c apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz.sha512; \
        rm -r apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz.sha512; \
        tar -zxvf apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz; \
        mv apache-activemq-${ACTIVEMQ_VERSION} /usr/local/apache-activemq; \
        rm apache-activemq-${ACTIVEMQ_VERSION}-bin.tar.gz
WORKDIR $ACTIVEMQ_HOME

EXPOSE 61616 8161

CMD ["activemq", "console"]
