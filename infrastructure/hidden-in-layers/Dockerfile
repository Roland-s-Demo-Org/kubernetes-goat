FROM alpine:3.24.3@sha256:be2656061b536c1883c4034790e21d0a09c5aaaf51968b89368a3c0371ea2c9a

LABEL MAINTAINER "Madhu Akula" INFO="Kubernetes Goat"

ADD secret.txt /root/secret.txt

RUN echo "Contributed by Rewanth Cool" >> /root/contribution.txt \
    && rm -rf /root/secret.txt

CMD ["sh", "-c", "tail -f /dev/null"]
