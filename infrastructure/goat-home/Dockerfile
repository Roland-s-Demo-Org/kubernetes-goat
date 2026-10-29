FROM alpine:3.24.3@sha256:be2656061b536c1883c4034790e21d0a09c5aaaf51968b89368a3c0371ea2c9a AS build
LABEL MAINTAINER="Madhu Akula" INFO="Kubernetes Goat"

WORKDIR /build
ENV HUGO_VERSION=0.84.0
ENV HUGO_BINARY=hugo_${HUGO_VERSION}_Linux-64bit.tar.gz
RUN set -x && \
  apk add --update wget git ca-certificates imagemagick && \
  if [ `uname -m` == "aarch64" ]; then \
      HUGO_BINARY=hugo_${HUGO_VERSION}_Linux-ARM64.tar.gz; \
  else \
      HUGO_BINARY=hugo_${HUGO_VERSION}_Linux-64bit.tar.gz; \
  fi; \
  wget https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/${HUGO_BINARY} && \
  tar xzf ${HUGO_BINARY} && \
  mv hugo /usr/bin

COPY home .

RUN git clone https://github.com/madhuakula/toc-page-hugo-theme.git themes/toc-page \
    && /usr/bin/hugo

FROM nginx:alpine-slim@sha256:f45171d36c76a8b2f5ef97108a3a8a2294248a6578a0a180edc2d78f7d2edc26
LABEL MAINTAINER="Madhu Akula" INFO="Kubernetes Goat"

COPY --from=build /build/public /usr/share/nginx/html
