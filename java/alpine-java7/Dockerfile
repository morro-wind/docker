FROM alpine:3.10

# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

ADD jre-7u80-linux-x64.tar.gz /usr/local/
# add a simple script that can auto-detect the appropriate JAVA_HOME value
# based on whether the JDK or only the JRE is installed
RUN { \
		echo '#!/bin/sh'; \
		echo 'set -e'; \
		echo; \
		echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; \
	} > /usr/local/bin/docker-java-home \
	&& chmod +x /usr/local/bin/docker-java-home
ENV JAVA_HOME /usr/local/jre1.7.0_80
ENV PATH $PATH:$JAVA_HOME/bin

ENV JAVA_VERSION 7u80

RUN set -eux; \
	find "$JAVA_HOME/lib" -name '*.so' -exec dirname '{}' ';' | sort -u > /etc/ld.so.conf.d/docker-jre.conf; \
	ldconfig; \
	\
# basic smoke test
	java -version
