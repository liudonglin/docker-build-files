FROM alpine:3.11

ARG VERSION_GCC=9.3.0-r0

RUN apk update \
    && apk add --no-cache gcc==${VERSION_GCC} \
    && apk add --no-cache g++==${VERSION_GCC} \
    && rm -rf /var/cache/apk/*

# docker build --rm=true -t liudonglin/alpine:3.11-gcc