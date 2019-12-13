FROM redis:3.2.10-alpine
COPY sentinel.conf /usr/local/etc/redis/sentinel.conf
CMD [ "redis-server", "/usr/local/etc/redis/sentinel.conf", "--sentinel" ]
