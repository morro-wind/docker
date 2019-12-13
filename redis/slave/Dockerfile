FROM redis:3.2.10-alpine
COPY redis.conf /usr/local/etc/redis/redis.conf
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf", "--slaveof redis-master 6379" ]
