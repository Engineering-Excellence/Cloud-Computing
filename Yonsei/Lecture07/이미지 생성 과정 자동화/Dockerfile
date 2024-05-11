FROM httpd:latest

RUN echo "<html><body><h1>Docker Build Test</h1></body></html>" > /usr/local/apache2/htdocs/index.html

ENTRYPOINT /usr/local/bin/httpd-foreground
