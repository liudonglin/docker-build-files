FROM alpine:latest

ENV JAVA_HOME=/usr/lib/jdk

# ADD和COPY的区别是ADD可以自动解压压缩包
ADD apache-maven-3.9.6-bin.tar.gz /usr/local/maven/
COPY ./settings.xml /root/.m2/

# Download and extract JDK 17
RUN wget -nv -O jdk.tar.gz https://aka.ms/download-jdk/microsoft-jdk-17-alpine-x64.tar.gz && \
    mkdir $JAVA_HOME && \
    tar xf jdk.tar.gz -C $JAVA_HOME --strip-components 1 --no-same-owner

# 设置环境变量
ENV MAVEN_HOME=/usr/local/maven/apache-maven-3.9.6
ENV MAVEN_CONFIG=/root/.m2

ENV PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin
