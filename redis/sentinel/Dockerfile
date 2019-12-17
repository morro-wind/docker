FROM redis:3.2.10-alpine
COPY sentinel.conf /usr/local/etc/redis/sentinel.conf
RUN chown -R redis.redis /usr/local/etc/redis
CMD [ "redis-server", "/usr/local/etc/redis/sentinel.conf", "--sentinel" ]
