FROM daocloud.io/library/php:7.2.9-alpine
RUN echo -e "http://mirrors.aliyun.com/alpine/latest-stable/main\nhttp://mirrors.aliyun.com/alpine/latest-stable/community" > /etc/apk/repositories \
    && cd /usr/local/bin && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install bcmath
