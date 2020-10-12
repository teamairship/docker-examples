# Docker - simple PHP server

Follow these steps to start the php server:

```
cd /path/to/example-php-apache
docker build -t example-php-apache-img .
docker run -p 3000:80 -v $(pwd)/src:/var/www/html --name example-php-apache-container example-php-apache-img
```

Open up the following url in your browser:

- http://localhost:3000


# Notes

In the `docker run` command:
- `-p` maps ports like so: `<MACHINE_PORT>:<CONTAINER_PORT>`
- `-v` specifies the volume to enable realtime updates in local dev environment.
  - The volume must be specified at runtime in order for this to work. [See documentation](https://docs.docker.com/engine/reference/builder/#notes-about-specifying-volumes) for more details.
  - The host volume mount src MUST be absolute, not relative
  - `$(pwd)` just outputs the absolute path of the present working directory
  - Volumes have ZERO effect once deployed (except for sharing filesystems across several containers)
