FROM golang:1.14-alpine as build

ARG TARGETPLATFORM
ARG VERSION=v1.18.2

WORKDIR /home/alpine

RUN apk add --no-cache git curl

RUN apk add --no-cache git curl jq \
    && addgroup -g 1000 alpine \
    && adduser -u 1000 -G alpine -h /home/alpine -s /bin/sh -D alpine


RUN curl -SsL -o /usr/local/bin/kubectl \
    "https://storage.googleapis.com/kubernetes-release/release/v${VERSION}/bin/linux/arm64/kubectl" \
    && chmod +x /usr/local/bin/kubectl

USER alpine:alpine

ENTRYPOINT [ "/usr/local/bin/kubectl" ]