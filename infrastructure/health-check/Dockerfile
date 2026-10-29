FROM golang:1.27.3@sha256:2920bb124f1a2e12a1d39f0cab756ae0068441ee1da7655dec7f5e374944095b
LABEL MAINTAINER="Madhu Akula" INFO="Kubernetes Goat"

WORKDIR /

COPY views /views
COPY go.mod /go.mod
COPY go.sum /go.sum
COPY main.go /main.go


RUN apt update && apt install curl wget iputils-ping -y
RUN go build -o /

EXPOSE 80

CMD ["/health-check"]
