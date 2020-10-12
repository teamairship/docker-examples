# Docker - simple PHP server

Based heavily off of these tutorials:

- [Learn Docker in 12 Minutes 🐳](https://www.youtube.com/watch?v=YFl2mCHdv24)
- [Docker Compose in 12 Minutes](https://www.youtube.com/watch?v=Qw9zlE3t8Ko)

Follow these steps to start the php server:

```
cd /path/to/example-php-apache
docker build -t example-php-apache-img .
docker run \
  -p 8000:80 \
  -v $(pwd)/src:/var/www/html \
  --name example-php-apache-container \
  example-php-apache-img
```

Open up the following url in your browser:

- http://localhost:8000


#### Notes about `docker run`:

- `-p` maps ports like so: `<MACHINE_PORT>:<CONTAINER_PORT>`
- `-v` specifies the volume to enable realtime updates in local dev environment.
  - The volume must be specified at runtime in order for this to work. [See documentation](https://docs.docker.com/engine/reference/builder/#notes-about-specifying-volumes) for more details.
  - The host volume mount src MUST be absolute, not relative
  - `$(pwd)` just outputs the absolute path of the present working directory
  - Volumes have ZERO effect once deployed (except for sharing filesystems across several containers)

## Docker Compose

All of the above can steps can be simplified into a single cmd that utilizes docker compose:

```
cd /path/to/example-php-apache
docker-compose up
```

## File changes during development

Normally, a docker image would need to be re-built in order for any changes to show up. Obviously this is not ideal for a local development environment.

The volume configuration specified above in the `docker run -v` command and in `docker-compose.yml` basically allow for the local machine and the docker container to share the same source files.

**NOTE** - if any changes added after the initial build, then `docker build` will need to be run again before deploying to a remote. Otherwise, the changes will not show up.
