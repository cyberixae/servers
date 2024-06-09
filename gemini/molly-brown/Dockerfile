FROM ubuntu
RUN apt-get update
RUN apt install --yes git golang
ADD https://tildegit.org/solderpunk/molly-brown.git molly-brown

WORKDIR molly-brown
RUN go build

RUN openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365 -nodes -subj '/CN=localhost' -addext 'subjectAltName = DNS:localhost'

EXPOSE 1965/tcp

ENTRYPOINT ./molly-brown -c example.conf
