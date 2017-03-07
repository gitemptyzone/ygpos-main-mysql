# ygpos-main-mysql
A Docker Composer to run mysql container for ygpos-backend application

If you want to communicate the application containers which is running under the nginx-procxy service, it is better to run under the same network.

Following part should be added to docker-compose.yml of each service:
```
networks:
  default:
    external:
      name: ${APPLICATION_NETWROK}
```
APPLICATION_NETWROK environment variable can be set on .env file or run following command:
```
$ export APPLICATION_NETWROK=<network name>
```

## Usage
- Clone or pull the latest version of this project.
- Create user-defined network which is used by related service containers.
```
$ docker network create --driver bridge <name of network>
```
If there is any application level network, you can skip this part, and use the nework.
- Copy .env.example to .env, then enter the name of created user-defined network.
```
APPLICATION_NETWROK=<name of network>
```
- Set the name of a container to CONTAINER_NAME environmet variable on .env
```
MYSQL_CONTAINER_NAME=<name or mysql container>
````
- Execute "docker-composer up" command to create a service container.