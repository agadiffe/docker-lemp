# docker-lemp

## Images
based on official:
- nginx:1.11.3-alpine
- php:7.0.9-fpm-alpine
- mariadb:10.1.16

before build, check if new version are available

if the official repo is not the last version, build your own image with a dockerfile  
simply copy the original dockerfile and change the version :D

then, in docker-compose.yml, in nginx services (or php, or mariadb), add:
```
build: 
	context: .
	dockerfile: nginx-last-version.dockerfile
```

## Config
### environment variables
```
cp mariadb.config.env.sample mariadb.config.env
cp php.config.env.sample php.config.env
```
then, change default value ...

### mariadb
read the official docker image doc  
(e.g. You can create db or user on init)

### nginx
you can have several site
- add dir in ./html (e.g. ./html/site2/)
- configure ./nginx/conf.d/site-available/site2.conf
- make symbolic link in site-enable
- use the same database or use another one
