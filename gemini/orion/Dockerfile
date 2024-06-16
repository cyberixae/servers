FROM ubuntu
RUN apt update
RUN apt install --yes golang make openssl

ADD https://codeberg.org/grisu48/orion.git orion
WORKDIR orion
RUN make
RUN openssl req -x509 -newkey rsa:2048 -keyout orion.key -out orion.crt -days 3650 -nodes -subj '/CN=localhost'

EXPOSE 1965/tcp

ENTRYPOINT ./orion -config orion.conf
