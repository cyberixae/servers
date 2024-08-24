FROM ubuntu:20.04
RUN apt update
RUN DEBIAN_FRONTEND=noninteractive apt install --yes cargo build-essential pkg-config openssl libssl-dev
ADD https://github.com/slogemann1/aerozine.git /aerozine
WORKDIR /aerozine
RUN cargo build
WORKDIR /aerozine/target/debug
RUN ./aerozine init -p server
WORKDIR /aerozine/target/debug/server/data
RUN openssl req -x509 -newkey rsa:4096 -keyout private.key -out certificate.crt -days 365 -nodes -sha256 -subj '/CN=localhost'
RUN openssl pkcs12 -export -out profile.pfx -inkey private.key -in certificate.crt -password pass:password
WORKDIR /aerozine/target/debug/server
RUN ls root

EXPOSE 1965/tcp

ENTRYPOINT ../aerozine
