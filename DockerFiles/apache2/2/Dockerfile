FROM ubuntu
RUN apt-get update
RUN apt-get install -y apache2 && apt-get clean
RUN echo "<html><header><title>This is title</title></header><body>Hello world</body></html>" >> /var/www/html/index.html
EXPOSE 80
CMD apachectl -D FOREGROUND
