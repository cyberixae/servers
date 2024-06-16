FROM ubuntu
RUN apt update
RUN apt install --yes cargo

ADD https://github.com/mbrubeck/agate.git agate
WORKDIR agate
RUN cargo build --release

EXPOSE 1965/tcp

ENTRYPOINT target/release/agate --hostname localhost
