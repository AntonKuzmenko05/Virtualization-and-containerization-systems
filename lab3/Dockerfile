FROM alpine:3.24

LABEL author="Anton Kuzmenko" \
      group="1254-пі-2" \
      version="1.0"

RUN apk add --no-cache apache2

COPY index.html /var/www/localhost/htdocs/index.html

EXPOSE 80

CMD ["httpd", "-D", "FOREGROUND"]