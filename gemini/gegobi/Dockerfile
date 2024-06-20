FROM ubuntu
RUN apt update
RUN apt install --yes git python3 #openssl

RUN git clone https://git.sr.ht/~solderpunk/gegobi
WORKDIR gegobi

RUN mkdir -p /var/gopher
RUN echo "Test page" > /var/gopher/index.gph

RUN openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes -subj '/CN=localhost'

EXPOSE 1965/tcp

ENTRYPOINT ./gegobi.py --host localhost
