# iNet Process Apache Docker Image for PHP FPM
Docker Hub: https://hub.docker.com/r/inetprocess/apache

Docker container containing Apache that connects to an FPM service.

## Usage
Add the following to your docker-compose.yml, assuming that your PHP VM is named `php` (see  [inetprocess/php](https://github.com/inetprocess/docker-php)).

```yaml
apache:
    image: inet/apache:2.2
    volumes:
        - ./www:/var/www
    ports:
        - 80:80
    links:
        - php


```


## Environment variables
Two variables have been created, to override the user and group that owns Apache (and all its files). 
That's useful if you need to mount a volume and own the files.

These environment variables are `APACHE_UID` and `APACHE_GID`. 


## Order of .htaccess
You can override an `.htaccess` file by putting an `.htaccess.local`, which could be interesting if you have to keep the main file in a git repository.


## Apache version
To use a specific Apache version, append the version number to the image name.
Eg: `image: inet/apache:2.2`

The following Apache versions are available:
* Apache 2.4 (jessie stable)
* Apache 2.2 (wheezy stable)
