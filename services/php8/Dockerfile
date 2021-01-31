ARG PHP_IMAGE
FROM ${PHP_IMAGE}
LABEL maintainer="hiPsyDuck<gdfs1996@qq.com>"

ARG GIT_NAME
ARG GIT_EMAIL

# 更换源
RUN sed -i "s/deb.debian.org/mirrors.aliyun.com/g" /etc/apt/sources.list 

# 核心扩展
RUN apt-get update && \
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libzip-dev zip git && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd && \
	docker-php-ext-install pdo_mysql && \
    docker-php-ext-install zip

# Redis 扩展
RUN pecl install -o -f redis-5.3.2 && \
rm -rf /tmp/pear && \
docker-php-ext-enable redis
    
# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

# Git
RUN git config --global user.name "${GIT_NAME}"
RUN git config --global user.email "${GIT_EMAIL}"

# 工作目录 
WORKDIR /var/www

# 权限设置
RUN usermod -u 1000 www-data