# WordPress on NGINX Unit
This is a sample configuration for running WordPress with NGINX Unit as the web server and PHP runtime. It is suitable for container-based demos and as a foundation for more serious environments.

It brings together the sample configuration from WordPress, Docker, and NGINX to create a simpler application stack for the frontend component.

NGINX Unit is the only daemon in the `wordpress:unit` Docker image. There is no Apache, no NGINX web server, no PHP-FPM - just Unit.

## Run the demo
#### 1. Clone this repo
#### 2. Start the backend (database) and frontent (Unit) containers
```shell
docker compose up -d
```
> _Add the `--build` option the first time to ensure a fresh image._

## Details
* The [Dockerfile](Dockerfile) is based on the official `unit-php` image, combined with the non-Apache parts of the [`wordpress:php8-apache` Dockerfile](https://github.com/docker-library/wordpress/blob/master/latest/php8.1/apache/Dockerfile).

* Unit's initial configuration is bootstrapped from [unitconf.json](unitconf.json). It is taken from the [Unit how-to documentation for WordPress](https://unit.nginx.org/howto/wordpress/)

* The `docker-compose.yaml` is based on [Docker's own quickstart guide for WordPress](https://docs.docker.com/samples/wordpress/).

* For convenience, Unit's configuration interface is exposed on [port 8080](docker-compose.yaml#L28). Without the `--control` parameter configuration is applied through the Unix socket in side the container.