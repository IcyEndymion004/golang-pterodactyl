FROM golang:1.24-alpine AS builder

RUN apk add --no-cache ca-certificates tzdata \
    && adduser -D -h /home/container container

RUN apt update -y && apt install -y \
    git \
    wget \
    curl \
    build-essential \
    ca-certificates \
 && rm -rf /var/lib/apt/lists/*
 
USER container
ENV USER=container HOME=/home/container
ENV GOPATH=/home/container/go
ENV GOCACHE=/home/container/.cache/go-build
ENV PATH=$GOPATH/bin:$PATH
WORKDIR /home/container

RUN mkdir -p /home/container/go /home/container/.cache/go-build

COPY entrypoint.sh /entrypoint.sh

CMD ["/bin/ash", "/entrypoint.sh"]
