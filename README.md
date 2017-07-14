# docker-lamp-php5.6
docker-composer settings for php5.6.

## Include
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

pre install docker-sync.

```
gem install docker-sync
brew install fswatch
brew install unison
```

Repository Download.

```
git clone git@github.com:murodon/docker-lamp-php5.6.git docker-lamp
cd docker-lamp
```
The .env file is settting for mysql user. 

`vi .env`

Next, build and start containers.

```
docker-sync-stack start
```

web:
localhost:9000

mailcatcher:
localhost:1025

```
docker exec -ti dockeropenpne_app_1 bash
```
