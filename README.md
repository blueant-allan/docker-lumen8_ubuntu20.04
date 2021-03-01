## Dockerfile development configuration for Lumen micro-framwork version 8.x using Ubuntu 20.04 as base image

Stack

* Ubuntu 20.04
* Lumen version 8.x
* Composer phar version 2.0.8
* Nginx
* PHP 7.4

Loaded PHP Extensions
* OpenSSL
* Mysql/PDO 
* Mbstring
* PHP Commons
* BCMath 
* JSON
* XML

## Compile the docker file

```
docker build -t lumen8.x-image -f Dockerfile.dev .
```

## Create instance of the container

```
docker run -p 8080:80 -dit --name container_name-web --mount type=bind,source="$(pwd)",target=/var/www/html lumen8.x-image
```

## Manage the container

```
docker exec -it container_name-web bash
```

## Usage

1. Start by creating a Lumen project via composer

```
composer create-project --prefer-dist laravel/lumen <project_name>
```

2. Build the dockerfile configuration and create a container for it.

3. Let us create a container for our new web-application

```
docker exec -it <project-name> bash

# let us complete the Lumen installation
php composer.phar install
```

4. You should be able to load your web-application from your browser. Example http://localhost:8080. And update your app-config file so you can connect to your database
