FROM ubuntu
RUN apt update
RUN apt install --yes golang openssl

ADD https://gitlab.com/lostleonardo/titan2.git titan2
WORKDIR titan2
RUN go build

run mkdir certs
RUN openssl req -x509 -newkey rsa:4096 -keyout certs/key.pem -out certs/crt.pem -days 365 -nodes -subj '/CN=localhost'

run mkdir gemini
RUN echo "# Test Page" > gemini/index.gmi

EXPOSE 1965/tcp

ENTRYPOINT ./titan2
