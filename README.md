# docker-eccube

[EC-CUBE3](http://www.ec-cube.net)  docker-compose sample for development

* sendmail missing

## Setup
```
$ git clone this repository
$ cd <project root>
$ wget http://downloads.ec-cube.net/src/eccube-3.0.10.zip
$ unzip eccube-3.0.10.zip
$ ln -s eccube-3.0.10 ec-cube
$ cd docker
$ // edit posrgres password in postgres/01_init.sql
$ docker-compose build
$ docker-compose up -d
$ docker-compose ps

      Name                 Command           State               Ports             
----------------------------------------------------------------------------------
docker_nginx_1      nginx -g daemon off;     Up      443/tcp, 0.0.0.0:8080->80/tcp 
docker_php_1        php-fpm                  Up      9000/tcp                      
docker_postgres_1   entrypoint.sh postgres   Up      5432/tcp


# browse install page
$ open http://localhost:8080/html/install.php
```

* step1: php extension auto check:  next
* step2: file/dir permission auto check: next
* step3: shop setting: input and next
* step4: database setting: input the below and next
    * hostname: postgres
    * port: 5432
    * dbname: cube3_dev
    * user: cube3_dev_user
    * password: ********** 
        * set the same password as docker/postgres/01_init.sql
* step5: database table initialization processed then redirected 
* step6: complete. go to admin page 
* admin: login 

```
# clean up
docker-compose stop
docker-compose rm -fv
```

