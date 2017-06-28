# docker-lamp5.6
Docker setting for php5.6.

- php:5.6-apache [dockerhub official]
    - iconv mcrypt pdo_mysql mbstring json xml tokenizer zip
- mysql:5.7 [dockerhub official]
- libfreetype6-dev
- libjpeg62-turbo-dev
- libmcrypt-dev
- libpng12-dev
- openssl libssl-dev
- libxml2-dev
- pecl
	- xdebug
	- APCu-4.0.10
	- redis

- vim
- git
- composer

- mailcatcher

## How to use

```
git clone git@github.com:murodon/docker-lamp5.6.git docker-lamp
cd docker-lamp
```
You can eddit the .env file.

`vi .env`

Next, build and start containers.

```
docker-compose up -d
```

web:
localhost:9000

mailcatcher:
localhost:1025

```
docker exec -ti dockeropenpne_app_1 bash
```
