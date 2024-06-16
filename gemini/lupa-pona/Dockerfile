FROM ubuntu
RUN apt update
RUN apt install --yes libfile-mimeinfo-perl libfile-slurper-perl libio-socket-ssl-perl libmodern-perl-perl libmojolicious-perl liburi-escape-xs-perl openssl

ADD https://github.com/kensanata/lupa-pona.git lupa-pona
WORKDIR lupa-pona
RUN openssl req -x509 -newkey ec -pkeyopt ec_paramgen_curve:prime256v1 -keyout key.pem -out cert.pem -days 1825 -nodes -subj '/CN=localhost'

EXPOSE 1965/tcp

ENTRYPOINT script/lupa-pona
