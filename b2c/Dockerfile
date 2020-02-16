# build --build-arg PARSE_DB_URI=dburl --bulid-arg API_BASE=apibase
FROM npm:pm2-test
LABEL maintainer="lie"

ARG PARSE_DB_URI
ARG API_BASE
ENV PARSE_DB_URI $PARSE_DB_URI
ENV API_BASE $API_BASE

COPY allInOne /opt/app/allInOne
RUN set -eux; \
	yarn install; \
	npm run build
