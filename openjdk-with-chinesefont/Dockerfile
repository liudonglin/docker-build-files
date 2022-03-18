FROM openjdk:8-jdk-alpine
RUN echo "http://mirrors.aliyun.com/alpine/v3.6/main" > /etc/apk/repositories \
    && echo "http://mirrors.aliyun.com/alpine/v3.6/community" >> /etc/apk/repositories \
    && apk update \
    && apk add font-adobe-100dpi \
    && mkdir /usr/share/fonts/chinese

COPY ./chinese-fonts/ /usr/share/fonts/chinese

# docker build -t liudonglin/openjdk:8-jdk-alpine-cn-fonts .