# SEE: https://hub.docker.com/_/php
FROM php:7.2-apache
LABEL maintainer="builders@teamairship.com"

# expose port 80 for http://
EXPOSE 80

# expose port 443 for https://
EXPOSE 443

# copy all files from src directory
COPY src/ /var/www/html/

# allow changes to auto-populate when running local dev environment
VOLUME src/ /var/www/html/
