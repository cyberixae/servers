FROM ubuntu
RUN apt-get update
RUN apt install --yes git golang openssl
ADD https://github.com/RealMelkor/Gemigit.git gemigit

WORKDIR gemigit
RUN go build

RUN openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365 -nodes -subj '/CN=localhost'

EXPOSE 1965/tcp

ENTRYPOINT ./gemigit
