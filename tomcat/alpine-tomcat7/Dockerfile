#Version: tomcat 7.0.96
FROM jdk:alpine-jdk7
LABEL maintainer="Morro Wind imorrowind@hotmail.com"

ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:/lib:/usr/lib
ENV TOMCAT_VERSION 7.0.96

# runtime dependencies for Tomcat Native Libraries
# Tomcat Native 1.2+ requires a newer version of OpenSSL than alpine:3.4 has available (1.0.2g+)
# see http://tomcat.10.x6.nabble.com/VOTE-Release-Apache-Tomcat-8-0-32-tp5046007p5046024.html (and following discussion)
RUN \
	apk add --no-cache --virtual .build-deps \
		gcc \
		libc-dev \
		make \
		openssl-dev \
		curl \
		gnupg \
		apr-dev \
		apr-util-dev \
	&& curl -fSL https://www.apache.org/dist/tomcat/tomcat-7/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz -o apache-tomcat-$TOMCAT_VERSION.tar.gz \
	&& curl -fSL https://www.apache.org/dist/tomcat/tomcat-7/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz.sha512 -o apache-tomcat-$TOMCAT_VERSION.tar.gz.sha512 \
	&& set -ex \
	&& sha512sum -c apache-tomcat-$TOMCAT_VERSION.tar.gz.sha512 \
	&& rm -r apache-tomcat-$TOMCAT_VERSION.tar.gz.sha512 \
	&& tar -xvf apache-tomcat-$TOMCAT_VERSION.tar.gz \
	&& mv apache-tomcat-$TOMCAT_VERSION /usr/local/tomcat \
	&& rm apache-tomcat-$TOMCAT_VERSION.tar.gz \
	&& cd /usr/local/tomcat \
	&& rm bin/*.bat \
	&& NATIVEBUILDDIR="$(mktemp -d)" \
	&& tar -xf bin/tomcat-native.tar.gz -C "$NATIVEBUILDDIR" \
	&& CONFIG=" \
		--libdir=/usr/lib \
		--prefix=/usr/local/tomcat \
		--with-apr=/usr/bin/apr-1-config \
		--with-java-home=$JAVA_HOME \
		--with-ssl=yes \
	" \
	&& ( \
		cd "$NATIVEBUILDDIR/tomcat-native-1.2.23-src/native" \
		&& pwd \
		&& ./configure $CONFIG \
		&& make \
		&& make install \
	) \
	&& cd $CATALINA_HOME \
	&& rm -rf "$NATIVEBUILDDIR" \
	&& rm bin/tomcat-native.tar.gz \
	&& apk del .build-deps \
	&& apk add --no-cache gettext apr \
	&& set -e \
		&& nativeLines="$(catalina.sh configtest 2>&1)" \
		&& nativeLines="$(echo "$nativeLines" | grep 'Apache Tomcat Native')" \
		&& nativeLines="$(echo "$nativeLines" | sort -u)" \
		&& if ! echo "$nativeLines" | grep 'INFO: Loaded APR based Apache Tomcat Native library' >&2; then \
			echo >&2 "$nativeLines"; \
			exit 1; \
		fi 
# COPY server.xml /usr/local/tomcat/conf/server.xml
WORKDIR $CATALINA_HOME

EXPOSE 8080

CMD ["catalina.sh", "run"]
