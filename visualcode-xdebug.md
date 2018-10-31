# Enabling VSCode and Xdebug inside Docker
PHP-FPM will be running inside a container, therefore your localhost IP will not work.
___

## Configuring Docker and Xdebug
*You need to change the placeholders on the `config/php-fpm/docker-php-ext-xdebug.ini` file.*

To get your machine IP, you can just search for it on your favorite search engine 
or you can run `ipconfig`  after getting your docker running. look for "Ethernet adapter vEthernet (DockerNAT)" 

___

## To search for the xdebug.so file, you can run  

```
docker-compose exec --user www-data phpfpm find /usr/local/lib/php/extensions -name xdebug.so
```

That will print the path for that file inside the docker image.  

You need to reboot your docker image after making these changes.

___

## VSCode 
After installing an add-on to debug PHP (we use [PHP Debug](https://github.com/felixfbecker/vscode-php-debug)), add the path of the docker image to your launch.json:
```
"pathMappings": {
    "/var/www/html": "${workspaceFolder}/wordpress",
}
```
