# Logstash plugin development in docker

This is a docker-compose application to develop a [Logstash](https://github.com/elastic/logstash) plugin inside Docker.

# Create and configure containers

## Using docker-compose

`docker-compose` simplifies Docker containers definition and configuration using definitions declared in `docker-compose.*-.yml` files.

Services declarations are splitted into following files, in order to be able to run only selected services:
- `docker-compose.yml` for logstash,
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
| `LOGSTASH_PLUGIN_HOME` | Directory of the Logstash plugin under development. | `./mounts/logstash-plugin` |

## Build application container

# Build and install plugin

## build using gem

## install plugin

# Test plugin
