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
$ open http://localhost:8080/install.php
```

* step1: php extension auto check:  next
* step2: file/dir permission auto check: next
* step3: shop setting: input and next
* step4: database setting: input the below and next
    * hostname: postgres
    * dbname: cube3_dev
    * user: cube3_dev_user
    * password: ********** 
        * set the same password as docker/postgres/01_init.sql
* step5: database table initialization processed then redirected 
* step6: complete. go to admin page
* admin: login


```
# Remove /html path prefix in URL
sed -i.bak \
  -e 's#^image_path: /html/#image_path: /#' \
  -e 's#^root_urlpath: null#root_urlpath: /#' \
  -e 's#^public_path: /html#public_path: /#' \
  ec-cube/app/config/eccube/path.yml
```

```
# stop container 
docker-compose stop

# clean up container (Note that -v option removes database container volume)
docker-compose rm -fv 
```

