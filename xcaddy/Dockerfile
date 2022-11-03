FROM golang AS builder
RUN go install github.com/caddyserver/xcaddy/cmd/xcaddy@latest &&\
    ./bin/xcaddy build --with github.com/caddyserver/forwardproxy@caddy2=github.com/klzgrad/forwardproxy@naive

#FROM ubuntu:22.04
FROM alpine:3.16
COPY --from=builder /go/caddy /usr/bin/
WORKDIR /xcaddy
COPY start.sh ./start.sh
RUN chmod +x ./start.sh
CMD ./start.sh