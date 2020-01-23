FROM node:8.15.0-alpine
LABEL maintainer="lie"

RUN set -eux; \
	npm config set unsafe-perm true; \
	npm install -g pm2; \
	apk --no-cache add make \
	python \
	g++ \
	gcc

WORKDIR /opt/app/allInOne
EXPOSE 3000
CMD [ "pm2", "start", "-n", "b2c", "--no-daemon", "npm -- run start" ]
