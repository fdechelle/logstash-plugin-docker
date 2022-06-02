# Logstash docker helper

This is a docker-compose application to run various Docker containers connected to logstash.

# Create and configure containers

## Using docker-compose

`docker-compose` simplifies Docker containers definition and configuration using definitions declared in `docker-compose.*-.yml` files.

Services declarations are splitted into following files, in order to be able to run only selected services:
- `docker-compose.beats.yml` for filebeat
- `docker-compose.nginx.yml` for nginx
- other files for other services to come

## Configuring containers to use

`docker-compose` command by default only uses file `docker-compose.yml`. 

To add more services defined in separate files, either:

- (recommended) specify list of configurations files into the `COMPOSE_FILE` variable in the `.env` configuration file, for example: `COMPOSE_FILE=docker-compose.yml:docker-compose.beats.yml`
- use the `docker-compose` command `--file /path/to/docker-compose.file.yml` option

## Defining configuration variables

Configuration variables can be defined using a `.env` file located in the same directory as `docker-compose.*-.yml` configuration files.

### Application container variables

All variables are described in the following table and have default values that makes their definition optionnal.

| Variable name | Description | Default value |
| --- | --- | --- |
| `NONE_YET` | None. | `NONE` |

## Running

### Running beats+nginx

Run logstash first:

```
sudo /usr/share/logstash/bin/logstash -f ./mounts/logstash/pipeline/beats/logstash.conf 
```

Then start beats+nginx containers, in a separate shell:

```
docker-compose up --file docker-compose.nginx.yml:docker-compose.beats.yml --remove-orphans
```

Then load http://192.168.56.106:8080 on host to visit Nginx home page.

Events should appear in logstash shell.

