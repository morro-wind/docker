# build --build-arg DB_URI=dburl --bulid-arg API_URI=apiurl
FROM npm:pm2-test
LABEL maintainer="lie"

ARG DB_URI
ARG API_URI
ENV DB_URI $DB_URI
ENV API_URI $API_URI

COPY nodejs /opt/nodejs
RUN set -eux; \
	yarn install; \
	npm run build
