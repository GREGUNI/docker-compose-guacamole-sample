# docker-compose-guacamole-sample

[Guacamole](https://guacamole.apache.org) is a really useful tool,
but can be difficult to setup properly. The deployment  process can be greatly
simplified using docker containers, and orchestrated using `docker-compose`.

## Usage

Assuming you already have a working Docker installation and `docker-compose`,
setup is really easy.

```
git clone git@github.com:GREGUNI/docker-compose-guacamole-sample.git
cd docker-compose-guacamole
docker-compose up
```
To start it as a daemon
```
docker-compose up -d
```

To stop it, if started as -d (otherwise Ctrl+C).
```
docker-compose down
```
To cleanup the data
```
docker-compose down --volume
```

Give it a few seconds to initialize and then you can access guacamole
at `http://docker-host:8080/guacamole/`. The default username and password are
both `guacadmin` (go to your user preferences to change it, and then create another user for regular use).

You _definitely_ want to open the `.env` file and change the example database passwords
before deploying this to anything resembling a production environment.

## The docker machines

`docker-compose` brings together several components to make this work.

- `db_1` - A MySQL container that acts as the database for all of
  guacamole's data.
- `guacd_1` - The guacamole server daemon (`guacd`) container that handles all the
  remote connections that guacamole makes.
- `guacamole_1` - The guacamole client web application container that ties
  everything together and provides the front-end for the user.

