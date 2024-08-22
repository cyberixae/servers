FROM ubuntu
RUN apt update
RUN apt install --yes git build-essential rustup

RUN git clone https://git.sr.ht/~zethra/stargazer stargazer
WORKDIR stargazer
RUN rustup default stable
RUN cargo install cargo-auditable
RUN ./scripts/build
RUN echo "[localhost]\nroot = ./test_data/test_site" >> config.ini

EXPOSE 1965/tcp

ENTRYPOINT target/release/stargazer config.ini
