FROM daocloud.io/library/php:7.2.9-fpm-alpine
RUN echo -e "http://mirrors.aliyun.com/alpine/latest-stable/main\nhttp://mirrors.aliyun.com/alpine/latest-stable/community" > /etc/apk/repositories \
    && cd /usr/local/bin && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath
EXPOSE 9000
CMD ["php-fpm"]
