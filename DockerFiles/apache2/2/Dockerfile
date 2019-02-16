FROM alpine:latest
LABEL maintainer="Marcin Skowron <marcin@skowron.io>"
LABEL description="This Dockerfile installs apache2."

RUN apt-get update
RUN apt-get install -y apache2 && apt-get clean
RUN echo "<html><header><title>This is title</title></header><body>Hello world</body></html>" >> /var/www/html/index.html

EXPOSE 80

ENTRYPOINT apachectl -D FOREGROUND
