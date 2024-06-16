FROM ubuntu
RUN apt update
RUN apt install --yes php

ADD https://codeberg.org/codeandcreate/JAGS-PHP.git jags-php
WORKDIR jags-php
RUN echo "<?php \$config=['hosts'=>['localhost'=>['root'=>'default','cert'=>'localhost.pem','cert_domain'=>'localhost']]];" > config.php
RUN openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes -subj '/CN=localhost'
RUN cat cert.pem key.pem > localhost.pem

EXPOSE 1965/tcp

ENTRYPOINT php server.php
