## Description

Minimal PHP Docker image focused on Laravel applications. It's use is intended for [Get In](https://github.com/getinapp), but can fit in any other PHP use-case.

#### About `composer`

> All images currently ship out with Composer 2.x.

## Available Tags

The image built is [`getinapp/php`](https://hub.docker.com/r/getinapp/php/tags) which has some tags available:

### 8.0

- [8.0](https://github.com/getinapp/php/blob/master/8.0/Dockerfile)

### 7.4

- [7.4](https://github.com/getinapp/php/blob/master/7.4/Dockerfile)

## Environment Variables

Variable | Default Value | Description
--- | --- | ---
**ASUSER** | `0` | Changes the user id that executes the commands

## Usage

With `docker run`:

```sh
docker run -it --rm getinapp/php:7.4 php -v
```

With environment variables:

```sh
docker run -it --rm -e ASUSER=1000 getinapp/php:7.4 php -v
```


With `docker-compose.yml`:

```yaml
app:
  image: getinapp/php:7.4
  ports:
    - "9773:9773"
  volumes:
    - ".:/var/www:cached"
    - "$HOME/.ssh/id_rsa:/home/developer/.ssh/id_rsa:cached"
  environment:
    ASUSER: "${$UID}"
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.