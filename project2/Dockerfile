# FROM ubuntu:20.04
# RUN apt-get update && apt-get install -y apache2
# COPY index.html /var/www/html/index.html
# COPY ./website/ /usr/local/apache2/htdocs/
# EXPOSE 80
# CMD ["apache2ctl", "-D", "FOREGROUND"]

FROM httpd:latest
COPY ./website/ /usr/local/apache2/htdocs/
EXPOSE 80
